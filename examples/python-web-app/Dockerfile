FROM ubuntu

# Set the working directory
WORKDIR /app

# Copy necessary files into the container
COPY requirements.txt /app
COPY devops /app

#RUN apt-get update && \
#    apt-get install -y python3 python3-pip && \
#    pip install -r requirements.txt && \
#    cd devops

# Update and install any system dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends python3-venv && \
    rm -rf /var/lib/apt/lists/*

# Create a virtual environment
RUN python3 -m venv venv

# Activate the virtual environment and install dependencies
RUN . venv/bin/activate && \
    pip install --upgrade pip && \
    pip install -r requirements.txt

# Set the virtual environment as the default for all future commands
ENV PATH="/app/venv/bin:$PATH"

# Specify the entrypoint and command to run the application
ENTRYPOINT ["python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]
