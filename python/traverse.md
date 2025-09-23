## Usage of Direction Vector
- 방향 벡터 (dx, dy)를 사전에 정의해서 사용하면, 순회 등의 문제를 풀 때 아주 용이하다!
```Python
def traverse_outward(matrix):
    """정방형 matrix 안에서 밖으로 순회"""
    current_x = current_y = len(matrix) // 2

    # 북동남서
    dx = [0, 1, 0, -1]
    dy = [-1, 0, 1, 0]
    dir_idx = 2

    current_count = 0  # 현재 방향으로 이동한 횟수
    length = 1  # 현재 방향으로 이동할 거리
    result = []
    result.append(matrix[current_y][current_x])

    # 서-남-동-북 순서로 순회
    while True:
        for _ in range(length):
            new_x = current_x + dx[dir_idx]
            new_y = current_y + dy[dir_idx]
            if new_x < 0 or new_x >= len(matrix) or new_y < 0 or new_y >= len(matrix):
                return result

            result.append(matrix[new_y][new_x])
            current_x, current_y = new_x, new_y

        # -1: 반시계, +1: 시계
        dir_idx = (dir_idx - 1) % 4
        current_count += 1
        # 현재 방향으로 이동한 횟수가 2번이면 이동할 거리를 1 증가
        if current_count == 2:
            length += 1
            current_count = 0


def traverse_inward(matrix, start=(0, 0)):
    """정방형 matrix 안에서 안으로 순회"""
    current_x, current_y = start

    # 북동남서
    dx = [0, 1, 0, -1]
    dy = [-1, 0, 1, 0]
    dir_idx = 0

    visited = [[False] * len(matrix) for _ in range(len(matrix))]

    result = []
    result.append(matrix[current_y][current_x])
    visited[current_y][current_x] = True

    while True:
        if len(result) == len(matrix) * len(matrix):
            return result

        while True:
            new_x = current_x + dx[dir_idx]
            new_y = current_y + dy[dir_idx]
            if new_x < 0 or new_x >= len(matrix) or new_y < 0 or new_y >= len(matrix):
                break
            elif visited[new_y][new_x]:
                break
            result.append(matrix[new_y][new_x])
            visited[new_y][new_x] = True
            current_x, current_y = new_x, new_y

        # -1: 반시계, +1: 시계
        dir_idx = (dir_idx - 1) % 4


if __name__ == "__main__":
    array = [
        [1, 2, 3, 4, 5],
        [5, 6, 7, 8, 9],
        [9, 10, 11, 12, 13],
        [13, 14, 15, 16, 17],
        [18, 19, 20, 21, 22],
    ]
    print(traverse_outward(array))
    print(traverse_inward(array, (len(array) - 1, len(array) - 1)))

```
