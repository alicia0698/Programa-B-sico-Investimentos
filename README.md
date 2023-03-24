# Programa-B-sico-Investimentos
Este é um programa básico desenvolvido em linguagem C,  criado para a simulação de investimentos, sendo o objetivo principal a execução efeitva das opções do sistema. 

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <locale.h>
#include <conio.h>
#include <math.h>
#define SIZE 200

char nome[50];
char cargo[SIZE][50];
char endereco[50];
char estado[50];
char setor[SIZE][50];
char data[SIZE][50];
char profissao[50];
char cidade[50];
char investidor[100], cpf[20];
int cpp[SIZE];
int op;
int tamanho;
int opcao, opcao_cad, opcao_rlt, opcao_crono, opcao_av;
int opcaoinvista;
int invalido;
int resp;
int contador = 0;
int tamanho;
int opcaologin;
int continuar;
int telademenu();
void cadastro();
void criptografia();
float acoes, compra, ir, liquido, previsao, previsto, bruto, inicial, mensal, meses, total, ano;


typedef struct{
    char login[30];
    char senha[30];
} pessoa; pessoa p[1];

int main()
{
    setlocale(LC_ALL, "Portuguese");
    system("Color B");

    int continuar = 1;
    	setlocale(LC_ALL, "");
    char login[30];
    char senha[30];
     relog:
    strcpy(p[0].login, "INV02624");
    strcpy(p[0].senha, "168705");
    	printf("              INVISTAC            \n\n");
    	printf("     CONTROLE DE GESTÃO INVISTA   \n\n");
    	printf("    ____________________________  \n");
    	printf("   |    > Primeiro Acesso <     | \n");
    	printf("   |    > Redefinir Senha <     | \n");
    	printf("   |____________________________| \n\n");
    	printf("  PARA ACESSAR INFORME LOGIN E SENHA  \n\n");
    	printf(" \n-> Login:  ");
    	scanf("%s", login);
    	printf(" \n-> Senha:  ");
    	scanf("%s", senha);
    	
    if ((strcmp(login,p[0].login)==0) && (strcmp(senha,p[0].senha)==0)){
        printf("\nUsuário logado");
        do
    {
        system("cls");
        printf("         INVISTAC         \n");
        printf("   Bem vindo, investidor!  \n\n");
        printf("   _____________________   \n");
        printf("  |        MENU         |  \n");
        printf("  |                     |  \n");
        printf("  |  1. Cadastro        |  \n");
        printf("  |  2. Relatórios      |  \n");
        printf("  |  3. Cronograma      |  \n");
        printf("  |  4. Avisos          |  \n");
        printf("  |_____________________|  \n\n\n");

        printf("  Escolha a opção desejada.\n  ");
        scanf("%d", &opcao);

        switch (opcao)
        {
        case 1:
            system("cls");
            telacadastro();
            break;

        case 2:
            system("cls");
            telainvista();
            break;

        case 3:
            system("cls");
            cronograma();
            break;

        case 4:
            system("cls");
            avisos();
            break;

        default:
            printf("  Comando inválido.\n");
        }
    } while (continuar);
    } else{
     printf("\n  (!) Login e/ou senha incorretos. Tecle para tentar novamente, ou acesse > redefinir senha < \n\n"); 
        getchar();
        system("pause");
        system("cls");
        goto relog;
    } while (continuar);

}

int telacadastro()
{
    static int linha;
    system("cls");
    printf("             CADASTRO            \n");
    printf("   _____________________________ \n");
    printf("  |                             |\n");
    printf("  |  1. Cadastro de cliente     |\n");
    printf("  |  2. Cadastro de funcionário |\n");
    printf("  |  0. Voltar                  |\n");
    printf("  |_____________________________|\n\n");

    printf("  Escolha a opção desejada.\n  ");
    scanf("%d", &opcao_cad);

    switch (opcao_cad)
    {
    case 1:
        system("cls");
        contador++;
        do
        {
            printf("                CADASTRO DE CLIENTE\n");
            printf("  __________________________________________________\n\n");
            printf("  Nome: ");
            fflush(stdin);
            fgets(nome, 50, stdin);
            nome[strlen(nome) - 1] = '\0';
            tamanho = strlen(nome);

            printf("  Profissão: ");
            fflush(stdin);
            fgets(profissao, 50, stdin);
            profissao[strlen(profissao) - 1] = '\0';
            tamanho = strlen(profissao);

            printf("  Endereço: ");
            fflush(stdin);
            fgets(endereco, 50, stdin);
            endereco[strlen(endereco) - 1] = '\0';
            tamanho = strlen(endereco);

            printf("  Cidade: ");
            fflush(stdin);
            fgets(cidade, 50, stdin);
            cidade[strlen(cidade) - 1] = '\0';
            tamanho = strlen(cidade);

            printf("  Estado: ");
            fflush(stdin);
            fgets(estado, 50, stdin);
            estado[strlen(estado) - 1] = '\0';
            tamanho = strlen(estado);

            printf("  CPF (Apenas números): ");
            scanf("%d", &cpf[linha]);

            printf("  __________________________________________________\n\n");

            printf("  Cadastro concluído.\n  Digite 1 para continuar ou 0 para sair.\n  ");
            scanf("%d", &op);
            linha++;
        } while (op == 1);
        return telacadastro();
        break;

    case 2:
        system("cls");
        contador++;
        do
        {
            printf("              CADASTRO DE FUNCIONÁRIO\n");
            printf("  __________________________________________________\n\n");
            printf("  Nome: ");
            fflush(stdin);
            fgets(nome, 50, stdin);
            nome[strlen(nome) - 1] = '\0';
            tamanho = strlen(nome);

            printf("  CPF (apenas números): ");
            scanf("%d", &cpp[linha]);

            printf("  Endereço: ");
            fflush(stdin);
            fgets(endereco, 50, stdin);
            endereco[strlen(endereco) - 1] = '\0';
            tamanho = strlen(endereco);

            printf("  Data de admissão: ");
            scanf("%s", &data[linha]);

            printf("  Setor: ");
            scanf("%s", &setor[linha]);

            printf("  Cargo: ");
            scanf("%s", &cargo[linha]);

            printf("  __________________________________________________\n\n");

            printf("  Cadastro concluido.\n  Digite 1 para continuar ou 0 para sair.\n  ");
            scanf("%d", &op);

            linha++;

        } while (op == 1);
        return telacadastro();
        break;
    }
}

int telainvista()
{
    system("cls");
    printf("            RELATÓRIOS           \n");
    printf("   _____________________________ \n");
    printf("  |                             |\n");
    printf("  |  1. Relatório de clientes   |\n");
    printf("  |  2. Relatórios da empresa   |\n");
    printf("  |  0. Voltar                  |\n");
    printf("  |_____________________________|\n\n");

    printf("  Aviso: Os relatórios serão descarregados em formato .txt\n");
    printf("  Escolha a opção desejada.\n  ");
    scanf("%d", &opcaoinvista);

    switch (opcaoinvista)
    {
    case 1:
        system("cls");
        contador++;
        do {
            system("cls");
            setlocale(LC_ALL, "Portuguese");
            printf("     RELATÓRIOS DE INVESTIMENTOS  \n");
            printf("   ______________________________ \n");
            printf("  |                              |\n");
            printf("  |  1. Ações                    |\n");
            printf("  |  2. Fundos de investimentos  |\n");
            printf("  |  3. Poupança                 |\n");
            printf("  |  4. Voltar                   |\n");
            printf("  |______________________________|\n\n");

            printf("  Escolha a opção desejada.\n  ");
            scanf("%d", &opcaoinvista);

            switch (opcaoinvista)
            {
            case 1:
                system("cls");
                contador++;
                do
                {
                    FILE *UNIP1;
                    UNIP1 = fopen("Investidores_Acao.txt", "a");
                    if (UNIP1 == NULL)
                    {
                        printf("  Erro na abertura do arquivo.");
                        system("pause");
                        return 0;
                    }
                    system("cls");
                    printf("                     AÇÃO DA INVISTAC                    \n");
                    printf("   _____________________________________________________ \n");
                    printf("  |                                                     |\n");
                    printf("  | Investimento de alto risto                          |\n");
                    printf("  | Valor da ação: R$ 12,50                             |\n");
                    printf("  | IR sobre a rentabilidade: 20%%                       |\n");
                    printf("  | Previsão de rentabilidade ao ano: 7%%                |\n");
                    printf("  | Taxa de administração sobre o total investido: Zero |\n");
                    printf("  |_____________________________________________________|\n\n");

                    printf("    Nome ou Razão Social: ");
                    fflush(stdin);
                    fgets(investidor, 100, stdin);
                    investidor[strlen(investidor) - 1] = '\0';
                    tamanho = strlen(investidor);
                    printf("    CPF ou CNPJ (apenas números): ");
                    scanf("%s", cpf);
                    printf("    Número de ações compradas: ");
                    scanf("%f", &compra);
                    acoes = (12.5 * compra);
                    printf("    Valor investimento em ações: R$ %.2f\n", acoes);
                    previsao = (0.07 * acoes);
                    printf("    Valor previsto de rentabilidade: R$ %.2f\n", previsao);
                    bruto = (previsao + acoes);
                    printf("    Valor bruto: R$ %.2f\n", bruto);
                    ir = (previsao * 0.2);
                    printf("    Valor do IR: R$ %.2f\n", ir);
                    liquido = (previsao - ir) + acoes;
                    printf("    Valor líquido: R$ %.2f\n", liquido);
                    printf("\n");

                    fprintf(UNIP1, "\tInvestidor de Acoes\n");
                    fprintf(UNIP1, "\n  Nome ou Razão Social: %s", investidor);
                    fprintf(UNIP1, "\n  CPF ou CNPJ: %s", cpf);
                    fprintf(UNIP1, "\n  Número de ações compradas: %.0f", compra);
                    fprintf(UNIP1, "\n  Valor do investimento em ações: R$ %.2f", acoes);
                    fprintf(UNIP1, "\n  Valor previsto de rentabilidade: R$ %.2f", previsao);
                    fprintf(UNIP1, "\n  Valor bruto: R$ %.2f", bruto);
                    fprintf(UNIP1, "\n  Valor do IR: R$ %.2f", ir);
                    fprintf(UNIP1, "\n  Valor: R$ %.2f", liquido);
                    fclose(UNIP1);

                    printf("    Dados gravados com sucesso!\n");
                    printf("    Digite 1 para continuar ou 0 para voltar.\n    ");
                    scanf("%d", &resp);
                } while (resp == 1);
                return telainvista();

                break;

            case 2:
                system("cls");
                contador++;

                do
                {
                    FILE *UNIP2;
                    UNIP2 = fopen("Investidores_FundoInvestimento.txt", "a");
                    if (UNIP2 == NULL)
                    {
                        printf("  Erro na abertura do arquivo.");
                        system("pause");
                        return 0;
                    }
                    system("cls");

                    printf("              FUNDO DE INVESTIMENTOS INVISTAC \n");
                    printf("   ______________________________________________________\n");
                    printf("  |                                                      |\n");
                    printf("  | Investimento de médio risco                          |\n");
                    printf("  | Tipo de taxa: pre-fixada                             |\n");
                    printf("  | Aplicação inicial a partir de R$ 0,00                |\n");
                    printf("  | IR sobre a rentabilidade: 15%%                        |\n");
                    printf("  | Previsão de rentabilidade ao ano: 24%% (2%% ao mes)    |\n");
                    printf("  | Taxa de administração sobre o total investido: Zero  |\n");
                    printf("  |______________________________________________________|\n\n");

                    printf("    Nome ou Razão Social: ");
                    fflush(stdin);
                    fgets(investidor, 100, stdin);
                    investidor[strlen(investidor) - 1] = '\0';
                    tamanho = strlen(investidor);
                    printf("    CPF ou CNPJ(apenas números): ");
                    scanf("%s", cpf);
                    printf("    Aplicação inicial: R$ ");
                    scanf("%f", &inicial);
                    printf("    Aplicação mensal: R$ ");
                    scanf("%f", &mensal);
                    printf("    Período em meses: ");
                    scanf("%f", &meses);
                    previsto = (inicial + mensal);
                    total = ((mensal * meses) + inicial);
                    printf("    Investimento total: R$ %.2f\n", total);
                    bruto = 1.02;
                    bruto = ((pow(bruto, meses)) * total);
                    printf("    Valor bruto: R$%.2f\n", bruto);
                    previsao = (bruto - total);
                    printf("    Rentabilidade:  R$ %.2f\n", previsao);
                    ir = (previsao * 0.15);
                    printf("    Valor IR: R$ %.2f\n", ir);
                    liquido = ((previsao - ir) + total);
                    printf("    Valor líquido: R$ %.2f\n", liquido);
                    printf("\n");

                    fprintf(UNIP2, "\tInvestidor de Fundos de Investimento\n");
                    fprintf(UNIP2, "\n  Nome ou Razão Social: %s", investidor);
                    fprintf(UNIP2, "\n  CPF ou CNPJ: %s", cpf);
                    fprintf(UNIP2, "\n  Aplicação inicial: R$ %.2f", inicial);
                    fprintf(UNIP2, "\n  Aplicação mensal: R $%.2f", mensal);
                    fprintf(UNIP2, "\n  Período em meses: %.0f", meses);
                    fprintf(UNIP2, "\n  Investimento total: R$ %.2f", total);
                    fprintf(UNIP2, "\n  Valor bruto: R$ %.2f", bruto);
                    fprintf(UNIP2, "\n  Rentabilidade: R$ %.2f", previsao);
                    fprintf(UNIP2, "\n  Valor IR: R$ %.2f", ir);
                    fprintf(UNIP2, "\n  Valor líquido: R$ %.2f", liquido);
                    fclose(UNIP2);

                    printf("    Dados gravados com sucesso!\n");
                    printf("    Digite 1 para continuar ou 0 para voltar.\n    ");
                    scanf("%d", &resp);
                } while (resp == 1);
                return telainvista();
                break;

            case 3:
                system("cls");
                contador++;
                do
                {
                    FILE *UNIP3;
                    UNIP3 = fopen("Investidores_Poupanca.txt", "a");
                    if (UNIP3 == NULL)
                    {
                        printf("  Erro na abertura do arquivo.");
                        system("pause");
                        return 0;
                    }
                    system("cls");
                    printf("\n");
                    printf("                    POUPANÇA INVISTAC                    \n");
                    printf("   ______________________________________________________\n");
                    printf("  |                                                      |\n");
                    printf("  | Investimento de baixo risco                          |\n");
                    printf("  | Aplicação inicial a partir de R$ 0,00                |\n");
                    printf("  | A conta poupança é isenta de IR                      |\n");
                    printf("  | Rentabilidade ao mês: 1%%                             |\n");
                    printf("  | Taxa de administração sobre o total investido: Zero  |\n");
                    printf("  |______________________________________________________|\n\n");

                    printf("    Nome ou Razão Social: ");
                    fflush(stdin);
                    fgets(investidor, 100, stdin);
                    investidor[strlen(investidor) - 1] = '\0';
                    tamanho = strlen(investidor);
                    printf("    CPF ou CNPJ (apenas números): ");
                    scanf("%s", cpf);
                    printf("    Aplicação inicial: R$ ");
                    scanf("%f", &inicial);
                    printf("    Aplicação mensal: R$ ");
                    scanf("%f", &mensal);
                    printf("    Período em meses: ");
                    scanf("%f", &meses);
                    total = ((mensal * meses) + inicial);
                    printf("    Investimento total: R$ %.2f\n", total);
                    bruto = (1 + 0.01);
                    bruto = (pow(bruto, meses) * total);
                    printf("    Valor bruto: R$%.2f\n", bruto);
                    previsao = (bruto - total);
                    printf("    Rentabilidade:  R$ %.2f\n", previsao);
                    liquido = (previsao + total);
                    printf("    Valor líquido: R$ %.2f\n", liquido);

                    fprintf(UNIP3, "\n");
                    fprintf(UNIP3, "\tInvestidor PoupanÃ§a \n");
                    fprintf(UNIP3, "\n  Nome ou RazÃ£o Social: %s", investidor);
                    fprintf(UNIP3, "\n  CPF ou CNPJ: %s", cpf);
                    fprintf(UNIP3, "\n  AplicaÃ§Ã£o inicial: R$ %.2f", inicial);
                    fprintf(UNIP3, "\n  AplicaÃ§Ã£o mensal: R $%.2f", mensal);
                    fprintf(UNIP3, "\n  Periodo em meses: %.0f", meses);
                    fprintf(UNIP3, "\n  Investimento total: R$ %.2f", total);
                    fprintf(UNIP3, "\n  Valor bruto: R$ %.2f", bruto);
                    fprintf(UNIP3, "\n  Rentabilidade: R$ %.2f", previsao);
                    fprintf(UNIP3, "\n  Valor liquido: R$ %.2f", liquido);
                    fclose(UNIP3);

                    printf("\n    Dados gravados com sucesso!");
                    printf("\n    Digite 1 para continuar ou 0 para voltar.\n    ");
                    scanf("%d", &resp);
                } while (resp == 1);
                return telainvista();
                break;

            case 4:
                return telainvista();
                break;
            default:
                printf("\n  Selecione uma opÃ§Ã£o vÃ¡lida.\n  Aperte ENTER ");
                system("pause");
                invalido = 1;
                break;
            }
        } while (invalido);

        system("pause");

    case 2:
        system("cls");
        contador++;
        system("cls");
        printf("         RELATÓRIOS DA EMPRESA        \n");
        printf("   __________________________________ \n");
        printf("  |                                  |\n");
        printf("  |  1. Desempenho 2 SEM/2021        |\n");
        printf("  |  2. Desempenho 1 SEM/2022        |\n");
        printf("  |  3. Remuneração de colaboradores |\n");
        printf("  |  4. Voltar                       |\n");
        printf("  |__________________________________|\n\n");

        printf("  Escolha a opção desejada.\n  ");
        scanf("%d", &opcaologin);

        switch (opcaologin)
        {
        case 1:
            system("cls");
            contador++;

            FILE *file;
            file = fopen("DESEMPENHO1.txt", "r");

            if (file == NULL)
            {
                printf("  Arquivo não encontrado.\n");
                system("pause");
                return 0;
            }

            char frase[10000];

            while (fgets(frase, 10000, file) != NULL)
            {
                printf("%s", frase);
            }

            fclose(file);
            break;

        case 2:
            system("cls");
            contador++;
            FILE *file1;
            file1 = fopen("DESEMPENHO2.txt", "r");

            if (file1 == NULL)
            {
                printf("  Arquivo não encontrado. \n");
                system("pause");
                return 0;
            }

            char frasee[10000];

            while (fgets(frasee, 10000, file1) != NULL)
            {
                printf("%s", frasee);
            }

            fclose(file1);
            break;

        case 3:
            system("cls");
            contador++;
            FILE *fileee;
            fileee = fopen("REM.txt", "r");

            if (fileee == NULL)
            {
                printf("  Arquivo não encontrado. \n");
                system("pause");
                return 0;
            }

            char fraseee[10000];

            while (fgets(fraseee, 10000, fileee) != NULL)
            {
                printf("%s", fraseee);
            }

            fclose(fileee);
            break;

        case 4:
            system("cls");
            break;

        default:
            telainvista();
        }
        system("pause");
        return telainvista();
    }
}

int cronograma() {
    printf("           CALENDÁRIO 2022\n");
    printf("   ______________________________\n");
    printf("  |           Novembro           |\n");
    printf("  |------------------------------|\n");
    printf("  |   D   S   T   Q   Q   S   S  |\n");
    printf("  |           1   2   3   4   5  |\n");
    printf("  |   6   7   8   9  10  11  12  |\n");
    printf("  |  13  14  15  16  17  18  19  |\n");
    printf("  |  20  21  22  23  24  25  26  |\n");
    printf("  |  27  28  29  30              |\n");
    printf("  |                              |\n");
    printf("  |            Datas             |\n");
    printf("  | 02 - Dia de Finados          |\n");
    printf("  | 15 - Proclamação da República|\n");
    printf("  | 21 - Atualização do sistema  |\n");
    printf("  | 28 - Apresentação InvistaC   |\n");
    printf("  |______________________________|\n\n\n");

    printf("   ______________________________\n");
    printf("  |           Dezembro           |\n");
    printf("  |------------------------------|\n");
    printf("  |   D   S   T   Q   Q   S   S  |\n");
    printf("  |                   1   2   3  |\n");
    printf("  |   4   5   6   7   8   9  10  |\n");
    printf("  |  11  12  13  14  15  16  17  |\n");
    printf("  |  18  19  20  21  22  23  24  |\n");
    printf("  |  25  26  27  28  29  30  31  |\n");
    printf("  |                              |\n");
    printf("  |            Datas             |\n");
    printf("  | 05 a 08 - 3* ExpoUni InvistaC|\n");
    printf("  | 09 - Suspensão do SAC        |\n");
    printf("  | 24 - Véspera de Natal        |\n");
    printf("  | 25 - Natal                   |\n");
    printf("  | 31 - Véspera Ano Novo        |\n");
    printf("  |______________________________|\n\n\n");

    printf("  Em caso de dúvidas, consulte os avisos da empresa.\n");
    printf("  Digite 0 para voltar.\n  ");
    scanf("%d", &opcao_crono);
}

int avisos() {
    printf("                   QUADRO DE AVISOS\n");
    printf("   _____________________________________________________\n");
    printf("  | Apresentação InvistaC                               |\n");
    printf("  |                                                     |\n");
    printf("  | A atualização e entrega, bem como a apresentação do |\n");
    printf("  | sistema InvistaC feita pela equipe será realizada   |\n");
    printf("  | presencialmente na Universidade Paulista de Santos, |\n");
    printf("  | no dia 28 de novembro de 2022.                      |\n");
    printf("  | Colaboradores responsáveis: Alicia, Andreza, Bianca,|\n");
    printf("  | Catarina, Nathalia e Tarcisio.                      |\n");
    printf("  |_____________________________________________________|\n\n");
    printf("   _____________________________________________________\n");
    printf("  | 3* ExpoUni InvistaC                                 |\n");
    printf("  |                                                     |\n");
    printf("  | Pelo terceiro ano consecutivo, a InvestC promove    |\n");
    printf("  | mais uma ExpoUni, uma exposição online para alunos  |\n");
    printf("  | do ensino médio e universitários de como o mercado  |\n");
    printf("  | financeiro opera, que acontecerá nos dias 05 e 08 de|\n");
    printf("  | dezembro.                                           |\n");
    printf("  |_____________________________________________________|\n\n");
    printf("   _____________________________________________________\n");
    printf("  | Suspensão do SAC                                    |\n");
    printf("  |                                                     |\n");
    printf("  | A equipe InvestC vem informar a suspensão de        |\n");
    printf("  | atividades de atendimento ao cliente a partir do dia|\n");
    printf("  | 09 de dezembro. Demais funções do software como     |\n");
    printf("  | informações para consulta  continuarão funcionando  |\n");
    printf("  |_____________________________________________________|\n\n");

    printf("  Em caso de dúvidas, consulte o cronograma da empresa.\n");
    printf("  Pressione 0 para voltar.\n  ");
    scanf("%d", &opcao_crono);
