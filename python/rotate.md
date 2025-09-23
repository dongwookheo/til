## Rotate 함수 구현
```Python
def rotate(matrix, option=1):
    """
    1: 90도 시계방향 회전
    2: 180도 회전
    3: 90도 반시계방향 회전 == 270도 시계방향 회전
    """
    r_n = len(matrix)
    c_n = len(matrix[0])

    if option % 4 == 1:
        new_matrix = [[0] * r_n for _ in range(c_n)]
        for r in range(r_n):
            for c in range(c_n):
                new_matrix[c][r_n - r - 1] = matrix[r][c]
    elif option % 4 == 2:
        new_matrix = [[0] * c_n for _ in range(r_n)]
        for r in range(r_n):
            for c in range(c_n):
                new_matrix[r_n - r - 1][c_n - c - 1] = matrix[r][c]
    elif option % 4 == 3:
        new_matrix = [[0] * r_n for _ in range(c_n)]
        for r in range(r_n):
            for c in range(c_n):
                new_matrix[c_n - c - 1][r] = matrix[r][c]
    else:
        new_matrix = [[0] * c_n for _ in range(r_n)]
        for r in range(r_n):
            for c in range(c_n):
                new_matrix[r][c] = matrix[r][c]

    return new_matrix


def rotate_zip(matrix, option=1):
    """
    1: 90도 시계방향 회전
    2: 180도 회전
    3: 90도 반시계방향 회전 == 270도 시계방향 회전
    """
    if option % 4 == 1:
        new_matrix = [list(row) for row in zip(*matrix[::-1])]
    elif option % 4 == 2:
        new_matrix = [row[::-1] for row in matrix[::-1]]
    elif option % 4 == 3:
        new_matrix = [list(row) for row in zip(*matrix)][::-1]
    else:
        new_matrix = [row[:] for row in matrix]

    return new_matrix
```
- Slicing 기능을 이용해, immutable 객체를 순회하도록 하면 마치 deep copy한 것과 같이 동작한다!
