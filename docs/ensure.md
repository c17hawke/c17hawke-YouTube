# Python good practices | Prevent unwanted bugs 

<iframe width="560" height="315" src="https://www.youtube.com/embed/roO5VGxOw2s" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


!!! note "installation"
    To install `ensure` run the following command:
    ```bash
    pip install ensure
    ```

## Code used in the demo

??? example "Code part 01 used in the video"
    ``` py title="demo.py" linenums="1"
    def is_product_is_positive(x: int, y: int) -> bool:
        if isinstance(x, int) and isinstance(y, int):
            if x*y >= 0:
                return True
            return False
        else:
            raise TypeError("x and y must be integers")

    result = is_product_is_positive(x=2, y=2)
    print(f"Case1: {result}")

    result = is_product_is_positive(x=2, y=22.2)
    print(f"Case2: {result}")

    result = is_product_is_positive(x=2, y="test")
    print(f"Case2: {result}")
    ```
??? example "Code part 02 used in the video"
    ``` py title="demo_ensure.py" linenums="1"
    from ensure import ensure_annotations

    @ensure_annotations
    def is_product_is_positive(x: int, y: int) -> bool:
        if x*y >= 0:
            return True
        return False

    # result = is_product_is_positive(x=2, y=2)
    # print(f"Case1: {result}")

    # result = is_product_is_positive(x=2, y=22)
    # print(f"Case2: {result}")

    # result = is_product_is_positive(x=2, y="test")
    # print(f"Case2: {result}")

    @ensure_annotations
    def get_product(x: int, y: int) -> int:
        return "x*y"

    result = get_product(x=2, y=22)
    print(f"Case1: {result}")
    ```