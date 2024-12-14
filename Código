#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define LIN 5
#define COL 5

int VALORES(unsigned char imagem[LIN][COL], int x, int y) {
    int lbp = 0;

    for (int i = -1; i <= 1; i++) {
        for (int j = -1; j <= 1; j++) {
            if (i == 0 && j == 0) {
                continue;
            }
            
            int vx = x + i;
            int vy = y + j;
            
            int vizinho = (vx >= 0 && vx < LIN && vy >= 0 && vy < COL) ? imagem[vx][vy] : 0;
            
            lbp = (lbp << 1) | (vizinho >= imagem[x][y]);
        }
    }
    return lbp;
}

void LBP(unsigned char imagem[LIN][COL], int imagem_lbp[LIN][COL]) {
    for (int i = 0; i < LIN; i++) {
        for (int j = 0; j < COL; j++) {
            imagem_lbp[i][j] = VALORES(imagem, i, j);
        }
    }
}

void HISTOGRAMA(int imagem_lbp[LIN][COL], int histograma[256]) {
    for (int i = 0; i < 256; i++) {
        histograma[i] = 0;
    }
    
    for (int i = 0; i < LIN; i++) {
        for (int j = 0; j < COL; j++) {
            histograma[imagem_lbp[i][j]]++;
        }
    }
}

int main() {
    unsigned char imagem[LIN][COL];
    int imagem_lbp[LIN][COL];
    int histograma[256] = {0};
    
    srand(time(NULL));

    for (int i = 0; i < LIN; i++) {
        for (int j = 0; j < COL; j++) {
            imagem[i][j] = rand() % 256;
        }
    }

    printf("Imagem de entrada:\n");
    for (int i = 0; i < LIN; i++) {
        for (int j = 0; j < COL; j++) {
            printf("%3d ", imagem[i][j]);
        }
        printf("\n");
    }
    puts("\n");

    LBP(imagem, imagem_lbp);
    HISTOGRAMA(imagem_lbp, histograma);

    printf("Imagem LBP:\n");
    for (int i = 0; i < LIN; i++) {
        for (int j = 0; j < COL; j++) {
            printf("%3d ", imagem_lbp[i][j]);
        }
        printf("\n");
    }
    puts("\n");

    printf("Histograma:\n");
    for (int i = 0; i < 256; i++) {
        if (histograma[i]) {
            printf("Valor %d: %d\n", i, histograma[i]);
        }
    }

    return 0;
}

