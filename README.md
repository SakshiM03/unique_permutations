# unique_permutations

def unique_permutations(arr):
    arr.sort()
    result = []
    used = [False] * len(arr)

    def backtrack(path):
        if len(path) == len(arr):
            result.append(path.copy())
            return

        for i in range(len(arr)):
            if used[i]:
                continue

            # Skip duplicate choices at the same level
            if i > 0 and arr[i] == arr[i - 1] and not used[i - 1]:
                continue

            used[i] = True
            path.append(arr[i])

            backtrack(path)

            path.pop()
            used[i] = False

    backtrack([])
    return result


numbers = [1, 1, 2]

for item in unique_permutations(numbers):
    print(item)

print("Total unique permutations:", len(unique_permutations(numbers)))
