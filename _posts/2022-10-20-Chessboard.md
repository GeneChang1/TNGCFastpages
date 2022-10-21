



<html>
    <head>
        <title></title>
        <meta charset="UTF-8">
        <style>
            .chess-board { border-spacing: 0; border-collapse: collapse; margin-left: 5%; margin-right: 15%;}
            .chess-board th { padding: 2em; }
            .chess-board td { border: 1px solid; width: 6em; height: 6em; text-align: center;}
            .chess-board .light { background: #FFFFFF; }
            .chess-board .dark { background: #808080; }
        </style>
    </head>
    <body>
        <table class="chess-board">
            <tbody>
                <tr>
                    <th></th>
                    <th>a</th>
                    <th>b</th>
                    <th>c</th>
                    <th>d</th>
                    <th>e</th>
                    <th>f</th>
                    <th>g</th>
                    <th>h</th>
                </tr>
                <tr>
                    <th>8</th>
                    <td class="light" id="a8"></td>
                    <td class="dark" id="b8"></td>
                    <td class="light" id="c8"></td>
                    <td class="dark" id="d8"></td>
                    <td class="light" id="e8"></td>
                    <td class="dark" id="f8"></td>
                    <td class="light" id="g8"></td>
                    <td class="dark" id="h8"></td>
                </tr>
                <tr>
                    <th>7</th>
                    <td class="dark" id="a7"></td>
                    <td class="light" id="b7"></td>
                    <td class="dark" id="c7"></td>
                    <td class="light" id="d7"></td>
                    <td class="dark" id="e7"></td>
                    <td class="light" id="f7"></td>
                    <td class="dark" id="g7"></td>
                    <td class="light" id="h7"></td>
                </tr>
                <tr>
                    <th>6</th>
                    <td class="light" id="a6"></td>
                    <td class="dark" id="b6"></td>
                    <td class="light" id="c6"></td>
                    <td class="dark" id="d6"></td>
                    <td class="light" id="e6"></td>
                    <td class="dark" id="f6"></td>
                    <td class="light" id="g6"></td>
                    <td class="dark" id="h6"></td>
                </tr>
                <tr>
                    <th>5</th>
                    <td class="dark" id="a5"></td>
                    <td class="light" id="b5"></td>
                    <td class="dark" id="c5"></td>
                    <td class="light" id="d5"></td>
                    <td class="dark" id="e5"></td>
                    <td class="light" id="f5"></td>
                    <td class="dark" id="g5"></td>
                    <td class="light" id="h5"></td>
                </tr>
                <tr>
                    <th>4</th>
                    <td class="light" id="a4"></td>
                    <td class="dark" id="b4"></td>
                    <td class="light" id="c4"></td>
                    <td class="dark" id="d4"></td>
                    <td class="light" id="e4"></td>
                    <td class="dark" id="f4"></td>
                    <td class="light" id="g4"></td>
                    <td class="dark" id="h4"></td>
                </tr>
                <tr>
                    <th>3</th>
                    <td class="dark" id="a3"></td>
                    <td class="light" id="b3"></td>
                    <td class="dark" id="c3"></td>
                    <td class="light" id="d3"></td>
                    <td class="dark" id="e3"></td>
                    <td class="light" id="f3"></td>
                    <td class="dark" id="g3"></td>
                    <td class="light" id="h3"></td>
                </tr>
                <tr>
                    <th>2</th>
                    <td class="light" id="a2"></td>
                    <td class="dark"  id="b2"></td>
                    <td class="light" id="c2"></td>
                    <td class="dark"  id="d2"></td>
                    <td class="light" id="e2"></td>
                    <td class="dark"  id="f2"></td>
                    <td class="light" id="g2"></td>
                    <td class="dark"  id="h2"></td>
                </tr>
                <tr>
                    <th>1</th>
                    <td class="dark" id="a1"></td>
                    <td class="light" id="b1"></td>
                    <td class="dark" id="c1"></td>
                    <td class="light" id="d1"></td>
                    <td class="dark" id="e1"></td>
                    <td class="light" id="f1"></td>
                    <td class="dark" id="g1"></td>
                    <td class="light" id="h1"></td>
                </tr>
            </tbody>
        </table>
    </body>
    <script>
        lettersOnBoard = "abcdefgh";
        chessBoard = {};
        //assigns the board
        for (j = 0; j <= 7; j++){
            letter = lettersOnBoard[j];
            for (i = 1; i <= 8; i++){
                var newKey = letter + i;
                chessBoard[newKey] = "O"
            }
        }
        chessBoard["a2"] = "wP";
        chessBoard["b2"] = "wP";
        chessBoard["c2"] = "wP";
        chessBoard["d2"] = "wP";
        chessBoard["e2"] = "wP";
        chessBoard["f2"] = "wP";
        chessBoard["g2"] = "wP";
        chessBoard["h2"] = "wP";
        chessBoard["a1"] = "wR";
        chessBoard["b1"] = "wKn";
        chessBoard["c1"] = "wB";
        chessBoard["d1"] = "wQ";
        chessBoard["e1"] = "wK";
        chessBoard["f1"] = "wB";
        chessBoard["g1"] = "wKn";
        chessBoard["h1"] = "wR";
        // piece class, to be extended by other classes
        class piece{
            constructor(_position, _color){
                this.position = _position;
                this.color = _color
            }
        }
        // rook class, a class for any new rook object. 
        class rook extends piece{
            constructor(_position, _color){
                // super is the position constructor, uh basically does some super cool inheritence stuff or something. 
                super(_position, _color);
                // automatically sets the spot on the board which is passed in to this rook
                this.setPosition();
                }
            //method to set the spot on the board to this piece based on this pieces current position
            setPosition(){
                chessBoard[this.position] = this.color + "R"
            }
            //method to return all of the available moves that the piece can make. 
            getTotalMoves(){
                let currentPosition = this.position.split("");
                let moves = [];
                for (var i = 1; i <= 8; i++){
                    var newMove = currentPosition[0] + i;
                    moves[i - 1] = newMove;
                }
                for (var i = 1; i <= 8; i++){
                    var newMove = lettersOnBoard[i - 1] + currentPosition[1];
                    moves.push(newMove);
                }  
                let totalMoves = [];
                moves.forEach((c) => {
                    if (c != this.position){
                        totalMoves.push(c);
                    }
                });
                return totalMoves;
            }   
            //method to return all of the obstructed moves based on the total moves
            getObstructedMoves(){
                let totalMoves = this.getTotalMoves();
                let obstructedMoves = [];
                for (var i = 0; i < totalMoves.length; i++){
                    if (chessBoard[totalMoves[i]] != "O"){
                        obstructedMoves.push(totalMoves[i]);
                    }
                }
                return obstructedMoves;
            }
            //method to return all of the moves which are not obstructed
            getFreeMoves(){
                let totalMoves = this.getTotalMoves();
                let obstructedMoves = this.getObstructedMoves();
                totalMoves.forEach((c) => {
                    //console.log(c);
                    for (var i = 0; i < obstructedMoves.length; i ++){
                        if (c == obstructedMoves[i]){
                            totalMoves.splice(totalMoves.indexOf(c), 1);
                        }
                    }
                })
                return totalMoves;
            }
            //method to return the pieces which can be captured. 
            getAvailableCaptures(){
                let totalMoves = this.getTotalMoves();
                let obstructedMoves = this.getObstructedMoves();
                let sameRow = [];
                let sameColumn = [];
                obstructedMoves.forEach((c) => {
                    if (this.position.split("")[0] == c.split("")[0]){
                        sameColumn.push(c);
                    }
                    else if (this.position.split("")[1] == c.split("")[1]){
                        sameRow.push(c);
                    }
                })
                console.log(sameColumn);
                console.log(sameRow);
                let columnNums = [];
                sameColumn.forEach((c) => {
                    //adds to a new array all of the numbers in the obstructed columns. Also converts it to an Integer
                    columnNums.push(parseInt(c.split("")[1]));
                })
                //elipses is a spread function, basically inputs each value in the array as it's own parameter. 
                var min = Math.min(...columnNums);
                var max = Math.max(...columnNums);
                var minPlace = sameColumn[columnNums.indexOf(min)];
                var maxPlace = sameColumn[columnNums.indexOf(max)];
                //Toby when you come back to this you need to subtract the current position and use the difference. You forgor :skull:
            }
        }
    //function to add the board to the table
    function getPiece(id) {
        document.getElementById(id).innerHTML = chessBoard[id];
    }
    //code that runs lol
    for (x in chessBoard){
        getPiece(x)
    }
    let rook1 = new rook("b1", "b");
    </script>
</html>