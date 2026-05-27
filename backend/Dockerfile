FROM manimcommunity/manim:stable

# Switch to root user to install dependencies
USER root

# Set the working directory
WORKDIR /app

# Copy requirements and install them
COPY requirements.txt /app/requirements.txt
RUN pip install --no-cache-dir -r /app/requirements.txt

# Copy the rest of the backend files
COPY . /app

# Ensure correct permissions for the manim user
RUN chown -R manim:manim /app

# Switch to manim user
USER manim

# Expose port (Render sets PORT env, defaults to 10000)
EXPOSE 10000

# Run uvicorn server
CMD ["sh", "-c", "uvicorn main:app --host 0.0.0.0 --port ${PORT:-10000}"]
