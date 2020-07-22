def add_matrices():
    n1, m1 = map(int, input('Enter size of first matrix: ').split())
    print('Enter first matrix:')
    A = [input().split() for i in range(n1)]
    n2, m2 = map(int, input('Enter size of second matrix: ').split())
    print('Enter second matrix:')
    B = [input().split() for i in range(n2)]
    if (n1, m1) == (n2, m2):
        C = [[float(A[i][j]) + float(B[i][j]) for j in range(m2)] for i in range(n2)]
        print('The result is:')
        for el in C:
            print(*el)
    else:
        print('The operation cannot be performed.')


def multiply_const():
    n, m = map(int, input('Enter size of first matrix: ').split())
    print('Enter first matrix:')
    A = [input().split() for i in range(n)]
    const = float(input('Enter constant: '))
    C = [[float(A[i][j]) * const for j in range(m)] for i in range(n)]
    print('The result is:')
    for el in C:
        print(*el)


def multiply_matrix():
    n1, m1 = map(int, input('Enter size of first matrix: ').split())
    print('Enter first matrix:')
    A = [input().split() for i in range(n1)]
    n2, m2 = map(int, input('Enter size of second matrix: ').split())
    print('Enter second matrix:')
    B = [input().split() for i in range(n2)]
    if m1 == n2:
        C = [[0 for _ in range(m2)] for _ in range(n1)]
        for i in range(n1):
            for j in range(m2):
                for k in range(m1):
                    C[i][j] += float(A[i][k]) * float(B[k][j])
        for el in C:
            print(*el)
    else:
        print('The operation cannot be performed.')


def transpose():
    print("""\n1. Main diagonal
2. Side diagonal
3. Vertical line
4. Horizontal line""")
    user_transp = int(input('Your choice: '))
    n, m = map(int, input('Enter matrix size: ').split())
    print('Enter matrix:')
    A = [input().split() for i in range(n)]
    if user_transp == 1:
        C = [[float(A[i][j]) for i in range(n)] for j in range(m)]
        for el in C:
            print(*el)
    elif user_transp == 2:
        C = [[float(A[i][j]) for i in range(n-1,-1,-1)] for j in range(m-1,-1,-1)]
        for el in C:
            print(*el)
    elif user_transp == 3:
        C = [[float(A[j][i]) for i in range(n-1,-1,-1)] for j in range(m)]
        for el in C:
            print(*el)
    elif user_transp == 4:
        C = [[float(A[j][i]) for i in range(n)] for j in range(m - 1, -1, -1)]
        for el in C:
            print(*el)


def calc_determin(matrix, mul):
    n = len(matrix)
    if n == 1:
        return mul * float(matrix[0][0])
    else:
        sign = -1
        determinant = 0
        for i in range(n):
            matr = []
            for j in range(1, n):
                elem = []
                for k in range(n):
                    if k != i:
                        elem.append(float(matrix[j][k]))
                matr.append(elem)
            sign *= -1
            determinant += mul * calc_determin(matr, sign * float(matrix[0][i]))
        return determinant


def inverse_matrix():
    n, m = map(int, input('Enter matrix size: ').split())
    print('Enter matrix:')
    A = [input().split() for i in range(n)]
    determin = calc_determin(A, 1)
    C = []
    for i in range(n):
        C.append([0] * m)
    for i in range(n):
        for j in range(n):
            minor = [[A[s][k] for k in range(n) if k != j] for s in range(0, n) if s != i]
            minor_float = calc_determin(minor, 1)
            C[i][j] = float(minor_float) * (-1)**(i+j)
    C_transp = [[(C[i][j]) for i in range(n)] for j in range(m)]
    const = 1/determin
    result = [[float(C_transp[i][j]) * const for j in range(m)] for i in range(n)]
    for el in result:
        print(*el)


def menu():
    while True:
        print("""\n1. Add matrices
2. Multiply matrix by a constant
3. Multiply matrices
4. Transpose matrix
5. Calculate a determinant
6. Inverse matrix
0. Exit""")
        user_choice = int(input('Your choice: '))
        if user_choice == 1:
            add_matrices()
        elif user_choice == 2:
            multiply_const()
        elif user_choice == 3:
            multiply_matrix()
        elif user_choice == 4:
            transpose()
        elif user_choice == 5:
            n, m = map(int, input('Enter matrix size: ').split())
            print('Enter matrix:')
            A = [input().split() for i in range(n)]
            if n != m:
                print('The operation cannot be performed.')
            else:
                print(calc_determin(A, 1))
        elif user_choice == 6:
            inverse_matrix()
        else:
            break

if __name__ == '__main__':
    menu()
