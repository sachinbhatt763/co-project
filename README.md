# co-project
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Global variables
int m[9] = {0}, w[9] = {0}, l[9] = {0}, p[9] = {0};
char *teams[] = {"RR", "DC", "PBKS", "KKR", "GT", "LSG", "CSK", "RCB", "MI", "SRH"};

void print_points_table(int team, int rank)
{
    switch (team)
    {
    case 0:
        printf("%d. RR             %d          %d       %d        %d\n", rank, m[team], w[team], l[team], p[team]);
        printf("****************************************************\n");
        break;
    case 1:
        printf("%d. DC             %d          %d       %d        %d\n", rank, m[team], w[team], l[team], p[team]);
        printf("****************************************************\n");
        break;
    case 2:
        printf("%d. PBKS           %d          %d       %d        %d\n", rank, m[team], w[team], l[team], p[team]);
        printf("****************************************************\n");
        break;
    case 3:
        printf("%d. KKR            %d          %d       %d        %d\n", rank, m[team], w[team], l[team], p[team]);
        printf("****************************************************\n");
        break;
    case 4:
        printf("%d. GT             %d          %d       %d        %d\n", rank, m[team], w[team], l[team], p[team]);
        printf("****************************************************\n");
        break;
    case 5:
        printf("%d. LSG            %d          %d       %d        %d\n", rank, m[team], w[team], l[team], p[team]);
        printf("****************************************************\n");
        break;
    case 6:
        printf("%d. CSK            %d          %d       %d        %d\n", rank, m[team], w[team], l[team], p[team]);
        printf("****************************************************\n");
        break;
    case 7:
        printf("%d. RCB            %d          %d       %d        %d\n", rank, m[team], w[team], l[team], p[team]);
        printf("****************************************************\n");
        break;
    case 8:
        printf("%d. MI             %d          %d       %d        %d\n", rank, m[team], w[team], l[team], p[team]);
        printf("****************************************************\n");
        break;
    case 9:
        printf("%d. SRH            %d          %d       %d        %d\n", rank, m[team], w[team], l[team], p[team]);
        printf("****************************************************\n");
        break;
    }
}

void manage_points_table()
{
    int count = 0, rank = 1, big = 0;
    printf("\n*************IPL-Indian Premier League*************\n");
    printf("\n                   Points table\n\n");
    printf("Team            Matches     Won    Lose    Points\n");
    printf("\n****************************************************\n");
    for (int i = 0; i < 10; i++)
    {
        for (int j = 0; j < 10; j++)
        {
            if (p[i] >= p[j])
            {
                count++;
                if (count == 10)
                {
                    big = p[i];
                }
            }
        }
        count = 0;
    }
repeat:
    for (int x = 0; x < 10; x++)
    {
        if (p[x] == big)
        {
            print_points_table(x, rank);
            rank++;
        }
        if (x == 9)
        {
            if (big == -5)
            {
                break;
            }
            else
            {
                big = big - 5;
                goto repeat;
            }
        }
    }
}

void calculate_points()
{
    int j, x, check, check1;
    char teamName[5];
    j = 5;
    for (int i = 0; i < 5; i++)
    {
    r:
        printf("%s Vs %s\n", teams[i], teams[j]);
        printf("Who won the match: ");
        scanf("%s", teamName);
        check = strcmp(teamName, teams[i]);
        check1 = strcmp(teamName, teams[j]);
        if (check == 0)
        {
            m[i] += 1;
            w[i] += 1;
            p[i] += 5;

            m[j] += 1;
            w[j] += 0;
            l[j] += 1;
            p[j] += 0;
        }
        else if (check1 == 0)
        {
            m[j] += 1;
            w[j] += 1;
            p[j] += 5;

            m[i] += 1;
            w[i] += 0;
            l[i] += 1;
            p[i] += 0;
        }
        else
        {
            printf("Invalid input, try again.\n");
            goto r;
        }
        j++;
    }
}

int main()
{
    int choose;
    do
    {
    again:
        printf("Press 1 to calculate points\n");
        printf("Press 2 to show points table\n");
        printf("Press 3 to exit\n");
        printf("Choose any option: ");
        scanf("%d", &choose);
        switch (choose)
        {
        case 1:
            calculate_points();
            break;
        case 2:
            manage_points_table();
            break;
        case 3:
            exit(0);
            break;
        default:
            printf("Invalid option, try again\n");
            goto again;
        }
    } while (choose != 3);

    return 0;
}
