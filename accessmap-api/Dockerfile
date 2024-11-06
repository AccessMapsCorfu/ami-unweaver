FROM python:3.7-alpine3.12

# Install dependencies required for building Python packages and the Rust compiler
RUN apk add --no-cache gcc musl-dev libffi-dev openssl-dev postgresql-dev curl

# Install Rust using rustup
RUN curl https://sh.rustup.rs -sSf | sh -s -- -y

# Set environment path for Rust
ENV PATH=/root/.cargo/bin:$PATH

# Upgrade pip and install Poetry
RUN pip install --upgrade pip && pip install poetry

# Copy project files to the container
COPY . /www/
WORKDIR /www/

# Install project dependencies using Poetry
RUN poetry install

# Set the command to run the application
CMD ["poetry", "run", "python", "run.py"]
