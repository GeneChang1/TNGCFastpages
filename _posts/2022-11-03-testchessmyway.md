<html>
    <script>
        class knight extends piece{
            constructor(_position, _color){
                super(_position, _color);
                this.id = "N";
                }
            //method to return all of the available moves that the piece can make. 
            getTotalMoves(){
                let currentPosition = this.position.split("");
                let moves = [];
                let aboveNum2 = parseInt(currentPosition[1]) + 2
                let currentLetNum = lettersOnBoard.indexOf(currentPosition[0])  
                for (var i = -1; i <= 1; i != 0; i++){
                    if (currentLetNum + i > -2 && currentLetNum + i < 8){
                        moves.push(lettersOnBoard[currentLetNum + i] + aboveNum2);
                    }
                }
                let aboveNum1 = parseInt(currentPosition[1]) + 1
                for (var i = -2; i <= 2; i != 0; i != 1; i != -1; i++){
                    if (currentLetNum + i != -1 && currentLetNum + i != 7 && aboveNum1 != 0){
                        moves.push(lettersOnBoard[currentLetNum + i] + aboveNum1);
                    }    
                }
                let belowNum1 = parseInt(currentPosition[1]) -1
                for (var i = -2; i <= 2; i != 0; i != 1; i != -1; i++){
                    if (i != 0 && currentLetNum + i != -1 && currentLetNum + i != 7){
                        moves.push(lettersOnBoard[currentLetNum + i] + belowNum1);
                    }
                }
                let belowNum2 = parseInt(currentPosition[1]) - 2
                let currentLetNum = lettersOnBoard.indexOf(currentPosition[0])  
                for (var i = -1; i <= 1; i != 0; i++){
                    if (currentLetNum + i > -2 && currentLetNum + i < 8){
                        moves.push(lettersOnBoard[currentLetNum + i] + belowNum2);
                return moves;
            }
            //method to return all of the obstructed moves based on the total moves
            getObstructedMoves(){
                let totalMoves = this.getTotalMoves();
                let obstructedMoves = [];
                totalMoves.forEach((c) => {
                    if (chessBoard[c][0] != "OO"){
                        obstructedMoves.push(c);
                    }
                })
                return obstructedMoves;
            }
            //method to return all of the moves which are not obstructed
            getFreeMoves(){
                let totalMoves = this.getTotalMoves();
                let obstructedMoves = this.getObstructedMoves();
                totalMoves = totalMoves.filter( (c) => !obstructedMoves.includes(c) );
                return totalMoves;
            }
            getAvailableCaptures(){
                let captures = [];
                let currentPosition = this.position.split(""); 
                let possibleLets = [
                    lettersOnBoard[lettersOnBoard.indexOf(currentPosition[0]) - 1],
                    lettersOnBoard[lettersOnBoard.indexOf(currentPosition[0]) + 1],
                    lettersOnBoard[lettersOnBoard.indexOf(currentPosition[0])]
                ];
                possibleLets = possibleLets.filter(c => c != undefined);
                possibleLets.forEach((c) => {
                    let a = parseInt(currentPosition[1]) + (1);
                        if (a != 9){
                            let check = c + a
                            console.log(check)
                            if (chessBoard[check][0][0] != this.color && chessBoard[check][0] != "OO"){
                                captures.push(check);
                        }
                    }
                    let b = parseInt(currentPosition[1]) - (1)
                        if (b != 0){
                            let check1 = c + b
                            console.log(check1)
                            if (chessBoard[check1][0][0] != this.color && chessBoard[check1][0] != "OO"){
                                captures.push(check1);
                        }
                    }
                    let d = parseInt(currentPosition[1])
                    let check2 = c + d
                    if (chessBoard[check2][0][0] != this.color && chessBoard[check2][0] != "OO"){
                        captures.push(check2);
                    }
                })
                return captures;
        }
    }
    <script>
<html>