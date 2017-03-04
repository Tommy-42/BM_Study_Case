<?php

class TaskWordHash {

        public function main() {

                $line = fgets(STDIN);
                $wordhash = new WordHash(json_decode($line, true));
        }
}


class WordHash {

        public function __construct($list) {

                $final = array();
                foreach($list as $k => $word) {
                        $final += $this->_findLetter($word, $list);

                }
                $this->_prettyPrint($final);
        }

        private function _findLetter($word, $list) {
                $tmp = array();

                for ($i = 0; $i < strlen($word); $i++) {
                        foreach($list as $k => $v) {

                                if (isset($tmp[$word])) {
                                        if( $v != $word && !in_array($v, $tmp[$word]) && in_array($word[$i], str_split($v)) ) {
                                                $tmp[$word][] = $v;
                                                continue;
                                        }
                                }
                                else {
                                        if( $v != $word && in_array($word[$i], str_split($v)) ) {
                                                $tmp[$word][] = $v;
                                                continue;
                                        }
                                }
                        }
                }
                return $tmp;

        }

        private function _prettyPrint($array) {

                echo "{\n";

                foreach($array as $word => $list) {
                        echo "  " . $word . " => [";

                        $last_key = end(array_keys($list));
                        foreach($list as $k => $wj) {
                                if( $k == $last_key)
                                        echo $wj;
                                else
                                        echo $wj . ', ';
                        }
                        echo "]\n";
                }

                echo "}\n";

        }
}
TaskWordHash::main();

?>