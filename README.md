# TIC-TACTOE-GAME
TIC TAC TOE GAME USING JAVA
import java.util.Scanner;

public class TicTacToe {
    static char[] board = {'1','2','3','4','5','6','7','8','9'};

    static void displayBoard() {
        System.out.println();
        System.out.println(" " + board[0] + " | " + board[1] + " | " + board[2]);
        System.out.println("---+---+---");
        System.out.println(" " + board[3] + " | " + board[4] + " | " + board[5]);
        System.out.println("---+---+---");
        System.out.println(" " + board[6] + " | " + board[7] + " | " + board[8]);
        System.out.println();
    }

    static boolean checkWin(char player) {
        int[][] wins = {
            {0,1,2}, {3,4,5}, {6,7,8},
            {0,3,6}, {1,4,7}, {2,5,8},
            {0,4,8}, {2,4,6}
        };

        for (int[] w : wins) {
            if (board[w[0]] == player &&
                board[w[1]] == player &&
                board[w[2]] == player) {
                return true;
            }
        }
        return false;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        char player = 'X';

        for (int turn = 0; turn < 9; turn++) {
            displayBoard();
            System.out.print("Player " + player +
                             ", choose position (1-9): ");
            int pos = sc.nextInt();

            if (pos < 1 || pos > 9 ||
                board[pos - 1] == 'X' ||
                board[pos - 1] == 'O') {
                System.out.println("Invalid position! Try again.");
                turn--;
                continue;
            }

            board[pos - 1] = player;

            if (checkWin(player)) {
                displayBoard();
                System.out.println("Player " + player + " wins!");
                sc.close();
                return;
            }

            player = (player == 'X') ? 'O' : 'X';
        }

        displayBoard();
        System.out.println("It's a draw!");
        sc.close();
    }
}