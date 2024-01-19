- from collections import Counter
def construct_tower(blocks, H):
    block_counts = Counter(blocks)
    sorted_blocks = sorted(block_counts.keys(), key=lambda x: (-block_counts[x], x))
    tower = []
    height = 0
    for block in sorted_blocks:
        block_height = block
        block_freq = block_counts[block]
        while block_freq > 0 and height + block_height <= H:
            tower.append(block_height)
            height += block_height
            block_freq -= 1
    return tower

# Example usage:
blocks = [1, 2, 3, 4, 5, 1, 2, 3, 4, 1, 2, 1]
H = 8
tower = construct_tower(blocks, H)
print("Constructed Tower Heights:", tower)
