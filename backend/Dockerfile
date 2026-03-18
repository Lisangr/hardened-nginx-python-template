FROM python:3.11-slim

# Create a non-root user
RUN groupadd -r appuser && useradd -r -g appuser appuser

# Set working directory
WORKDIR /app

# Copy the application file
COPY app.py .

# Change ownership to appuser
RUN chown -R appuser:appuser /app

# Switch to non-root user
USER appuser

# Expose port (for documentation purposes)
EXPOSE 8080

# Health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
    CMD python -c "import socket; socket.create_connection(('localhost', 8080), timeout=1)" || exit 1

# Start the application
CMD ["python", "app.py"]
