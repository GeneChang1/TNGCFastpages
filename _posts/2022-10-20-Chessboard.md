---
toc: false
layout: post
categories: [project]
title: Chess
---
<a href="https://www.chess.com/learn-how-to-play-chess">
    <button>How do I play chess?<button>
<a href="{{ site.baseurl }}/2022/10/23/Feedback.html">
    <button>Report an Issue<button>
<html>
    <head>
        <title></title>
        <meta charset="UTF-8">
        <style>
            .chess-board { border-spacing: 0; border-collapse: collapse; margin-left: 0%; margin-right: 5%;}
            .chess-board th { padding: 2em; }
            .chess-board td { border: 1px solid; width: 1em; height: 1em; text-align: center;}
            .chess-board .light { background: #FFFFFF; }
            .chess-board .dark { background: #808080; }
        </style>
    </head>
    <body>
        <table class="chess-board" id="chess-board">
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
                chessBoard[newKey] = "OO"
            }
        }
        for (x in lettersOnBoard){
            newPawn = lettersOnBoard[x] + "2";
            chessBoard[newPawn] = "wP";
        }
        chessBoard["a1"] = "wR";
        chessBoard["b1"] = "wN";
        chessBoard["c1"] = "wB";
        chessBoard["d1"] = "wQ";
        chessBoard["e1"] = "wK";
        chessBoard["f1"] = "wB";
        chessBoard["g1"] = "wN";
        chessBoard["h1"] = "wR";
        for (x in lettersOnBoard){
            newPawn = lettersOnBoard[x] + "7";
            chessBoard[newPawn] = "bP";
        }
        chessBoard["a8"] = "bR";
        chessBoard["b8"] = "bN";
        chessBoard["c8"] = "bB";
        chessBoard["d8"] = "bQ";
        chessBoard["e8"] = "bK";
        chessBoard["f8"] = "bB";
        chessBoard["g8"] = "bN";
        chessBoard["h8"] = "bR";
        chessBoard["d5"] = "OO";
        // assigns chess piece codes to their emoji 
        let chessPieces = {
            wP: "♙",
            wR: "♖",
            wN: "♘",
            wB: "♗",
            wQ: "♕",
            wK: "♔",
            OO: "",
            bP: "♟",
            bR: "♜",
            bN: "♞",
            bB: "♝",
            bQ: "♛",
            bK: "♚",
        }
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
            move(move){
                if(this.getFreeMoves().includes(move)) {this.position = move;}
                this.setPosition();
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
                // defines new variables as other methods in this class which may be useful.
                let totalMoves = this.getTotalMoves();
                let obstructedMoves = this.getObstructedMoves();
                // defines arrays
                let sameRow = [];
                let sameColumn = [];
                let columnNums = [];
                let columnDifs = [];
                let negDifsColumn = [];
                let posDifsColumn = [];
                let rowLets = [];
                let rowNums = [];
                let rowDifs = [];
                let posDifsRow = [];
                let negDifsRow = [];
                let captures = [];
                let finalCaptures = [];
                // finds all of the moves which are in the same row or in the same column as the rook.
                obstructedMoves.forEach((c) => {
                    if (this.position.split("")[0] == c.split("")[0]){
                        sameColumn.push(c);
                    }
                    else if (this.position.split("")[1] == c.split("")[1]){
                        sameRow.push(c);
                    }
                })
                //adds to a new array all of the numbers in the obstructed columns. Also converts it to an Integer
                sameColumn.forEach((c) => {
                    columnNums.push(parseInt(c.split("")[1]));
                })        
                //elipses is a spread function, basically inputs each value in the array as it's own parameter. 
                //this foreach finds the difference between the pieces in the same column and the rooks current position
                columnNums.forEach((c) => {columnDifs.push(c - parseInt(this.position.split("")[1]))});
                //this foreach defines two new
                columnDifs.forEach((c) => {if (c < 0) negDifsColumn.push(Math.abs(c)); else posDifsColumn.push(c);})
                // finds the minimum positive number and the minimum negative number and converts them to an integer
                var posMinColumn = parseInt(Math.min(...posDifsColumn));
                var negMinColumn = parseInt(Math.min(...negDifsColumn));
                // works backwards to find the position on the board given the smallest differences 
                sameColumn.forEach((c) => {if (parseInt(c.split("")[1]) == parseInt(this.position.split("")[1]) + posMinColumn || parseInt(c.split("")[1]) == parseInt(this.position.split("")[1]) - negMinColumn){captures.push(c)}})
                // basically does all of the same stuff but for the rows using the index of the lettersOnBoard array
                sameRow.forEach((c) => {rowLets.push(c.split("")[0]);})
                rowLets.forEach((c) => {rowNums.push(lettersOnBoard.indexOf(c) + 1)})
                rowNums.forEach((c) => {rowDifs.push(parseInt(c) - (lettersOnBoard.indexOf(this.position.split("")[0]) + 1))})
                rowDifs.forEach((c) => {if (c < 0) negDifsRow.push(Math.abs(c)); else posDifsRow.push(c);})
                var posMinRow = parseInt(Math.min(...posDifsRow));
                var negMinRow = parseInt(Math.min(...negDifsRow))
                sameRow.forEach((c) => {if ((lettersOnBoard.indexOf(c.split("")[0]) + 1) == (lettersOnBoard.indexOf(this.position.split("")[0]) + posMinRow + 1) || (lettersOnBoard.indexOf(c.split("")[0]) + 1) == (lettersOnBoard.indexOf(this.position.split("")[0]) - negMinRow + 1)){captures.push(c)}})
                //checks if captures are the same color or not
                captures.forEach((c) => {
                    if (chessBoard[c].split("")[0] != this.color){
                        finalCaptures.push(c);
                    }
                })
                return finalCaptures
            }   
        }
        //function to add the board to the table
        function movePiece(id){
            chessBoard["d5"] = "bR";
            document.getElementById(id).innerHTML = chessPieces[chessBoard[id].split("")[0]+chessBoard[id].split("")[1]];
        }
        function getPiece(id) {
            document.getElementById(id).innerHTML = chessPieces[chessBoard[id].split("")[0]+chessBoard[id].split("")[1]];
            document.getElementById(id).style.fontSize = "100px";
            document.getElementById(id).size = "10px";
            document.getElementById(id).onClick = function(){movePiece(id)};
        }
        //defines new rook object
        //let rook1 = new rook("b1", "w");
    </script>
    <script>
    </script>
    <script>
        for (x in chessBoard){
            getPiece(x)
        }
    </script>
</html>