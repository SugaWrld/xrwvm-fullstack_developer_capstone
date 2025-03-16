    # ---------------------------------------
    # Base Image
    # ---------------------------------------
    FROM python:3.12.0-slim-bookworm

    # ---------------------------------------
    # Environment Variables
    # ---------------------------------------
    ENV PYTHONUNBUFFERED=1
    ENV PYTHONWRITEBYTECODE=1
    ENV APP=/app

    # ---------------------------------------
    # Set Working Directory
    # ---------------------------------------
    WORKDIR $APP

    # ---------------------------------------
    # Install Dependencies
    # ---------------------------------------
    # Ensure pip is up-to-date
    RUN pip install --upgrade pip

    # Copy requirements and install them
    COPY requirements.txt $APP/
    RUN pip install -r requirements.txt

    # ---------------------------------------
    # Copy Project Files
    # ---------------------------------------
    COPY . $APP/

    # ---------------------------------------
    # Expose Port
    # ---------------------------------------
    EXPOSE 8000

    # ---------------------------------------
    # Make Entrypoint Executable
    # ---------------------------------------
    RUN chmod +x /app/entrypoint.sh

    # ---------------------------------------
    # Entrypoint Script (Optional Setup Tasks)
    # ---------------------------------------
    ENTRYPOINT ["/bin/bash", "/app/entrypoint.sh"]

    # ---------------------------------------
    # Start Django App with Gunicorn
    # ---------------------------------------
    CMD ["gunicorn", "--bind", ":8000", "--workers", "3", "djangoproj.wsgi"]
