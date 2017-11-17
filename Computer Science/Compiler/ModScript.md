# ModScript Case Study

```

<?php


/*
PrintScreen('TEST11111');
    PrintScreen('\n');
    PrintScreen(
        GivenCase(
            ('QWE'),
            [
                ['CASE1', 'TEST1'],
                ['CASE2', 'TEST2']
            ],
            'DEFAULT'
        )
    );
*/


$syntax = "

<@ModScript
    
    PrintScreen('LOOB');
    PrintScreen('\n');
    
    IncludeModScript('/home/cg/root/TestModeScript.mdscx');
    
@>

";

$comp = new Compiler();
$syntax = $comp->processedSyntax($syntax);
$comp->evaluateSyntax($syntax);

class Compiler {
    
    protected $reserveWords = [
        'PrintScreen',
        'GivenCase',
        'GivenIf',
        'IncludeModScript'
    ];
    
    public function processedSyntax($syntax) { // Lexical
        $syntax = preg_replace('/<@ModScript|@>|\/\*(\n|.)*\*\/|\/\/.*/', '', $syntax); //clear PL tag and comments
        
        $count = count($this->reserveWords);
        for ($x = 0; $x < $count; $x++) {
            $syntax = str_replace($this->reserveWords[$x], '$this->'.$this->reserveWords[$x], $syntax);     
        }
          
        return $syntax;
    }
    
    public function evaluateSyntax($syntax) { // Syntactic

        $syntax = trim($syntax);
        $syntax = (!$syntax) ? "'empty syntax';" : $syntax;
            
        var_dump($syntax);
        
        $result = '';
        eval("\$result = $syntax");
        return $result;
    }
    
    public function PrintScreen($subject) {
        
        echo $subject;
    }
    
    public function GivenCase($condition, $cases, $default) {
        
        $casesCount = count($cases);
        
        for ($x = 0; $x < $casesCount; $x++) {
            $caseCondition = ($condition == $cases[$x][0]);

            if ($caseCondition) {
                return $cases[$x][1]; 
            }
        }
        
        return $default;
    }
    
    public function GivenIf($condition, $statementTrue, $statementFalse) {
        
        $statement = '';
        
        if ($condition) {
            $statement = $statementTrue;
        } else {
            $statement = $statementFalse; 
        }

        return $statement;
    }
    
    public function IncludeModScript($path) {
        
        $file = file_get_contents($path);
        $syntax = $this->processedSyntax($file);
        $this->evaluateSyntax($syntax);
    }
}

// function run($f){
//     $f();
// }

// // and then we can use it like this:
// run(function(){
//     echo "do something";
// });

```