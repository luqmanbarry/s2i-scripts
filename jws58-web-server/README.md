# Override s2i/assemble script

To reuse the assemble script without having to build again within the Dockerfile, follow these steps:

1. Comment out the build steps inside the assemble script

2. Add these lines in the Dockerfile

    ```bash
    # Copy and override assemble script
    COPY .s2i/bin/assemble /usr/local/s2i/assemble
    RUN chmod +x /usr/local/s2i/assemble
    
    # Build application
    COPY . /tmp/src
    RUN /usr/local/s2i/assemble
    ```
