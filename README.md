# /\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/

# THIS REPO IS NO LONGER USED. DOCS ARE IN AXIOM-CO

# /\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/


# Axiom Documentation

This repository contains the documentation website code and Markdown source files for **https://docs.axiom.co/**

To file a docs issue, use the issue tracker in the [Axiom/docs](https://github.com/axiomhq/docs/issues/new) repo.

## Mkdocs Commands

- `mkdocs new [dir-name]` - Create a new project.
- `mkdocs serve` - Start the live-reloading docs server.
- `mkdocs build` - Build the documentation site.
- `mkdocs -h` - Print help message and exit.

For full documentation on Mkdocs visit [mkdocs.org](https://www.mkdocs.org).

---

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.

## How to Write Code Blocks
```

=== "Bash"
    ``` bash
    #!/bin/bash

    echo "Hello world!"
    ```

=== "C"
    ``` c
    #include <stdio.h>

    int main(void) {
      printf("Hello world!\n");
      return 0;
    }
    ```

=== "C++"
    ``` c++
    #include <iostream>

    int main(void) {
      std::cout << "Hello world!" << std::endl;
      return 0;
    }
    ```

=== "C#"
    ``` c#
    using System;

    class Program {
      static void Main(string[] args) {
        Console.WriteLine("Hello world!");
      }
    }
    ```

===! "Bash"
    ``` bash 
    #!/bin/bash

    echo "Hello world!"
    ```

=== "C"
    ``` c
    #include <stdio.h>

    int main(void) {
      printf("Hello world!\n");
      return 0;
    }
    ```

=== "C++"
    ``` c++
    #include <iostream>

    int main(void) {
      std::cout << "Hello world!" << std::endl;
      return 0;
    }
    ```

=== "C#"
    ``` c#
    using System;

    class Program {
      static void Main(string[] args) {
        Console.WriteLine("Hello world!");
      }
    }
    ```

```

## License

&copy; Axiom, Inc., 2021

Distributed under MIT License (`The MIT License`).

See [LICENSE](LICENSE) for more information.
