# Option 1: Amazon Corretto (Amazon's OpenJDK distribution)
FROM amazoncorretto:8

# Option 2: Azul Zulu (well-known for ARM support)
# FROM azul/zulu-openjdk:8

# Option 3: BellSoft Liberica (good ARM support)
# FROM bellsoft/liberica-openjdk-debian:8

# Option 4: Using arm64v8 specific image
#FROM arm64v8/openjdk:8-jdk

# Install required dependencies
RUN yum update -y && \
    yum install -y \
    gcc \
    gcc-c++ \
    make \
    libffi-devel \
    && yum clean all

# Create app directory
WORKDIR /app

# Copy the JAR file from the correct target location
# Note: Make sure to build the JAR before building the Docker image
COPY tools.descartes.dlim.httploadgenerator/target/httploadgenerator.jar app.jar

# Set library path and other environment variables
ENV LD_LIBRARY_PATH=/usr/lib:/usr/local/lib
ENV JAVA_TOOL_OPTIONS="-Djava.library.path=/usr/lib:/usr/local/lib"

ENTRYPOINT ["java","-jar","/app/app.jar"] 