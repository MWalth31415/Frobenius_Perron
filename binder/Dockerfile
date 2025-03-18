# Use Julia 1.11.4 as the base image
FROM julia:1.11.4

# Set the working directory
WORKDIR /home/julia

# Copy the Project.toml and Manifest.toml to set up the Julia environment
COPY Project.toml Manifest.toml ./

# Install dependencies
RUN julia -e 'using Pkg; Pkg.instantiate()'


# Install Pluto
RUN julia -e 'using Pkg; Pkg.add("Pluto"); Pkg.add("IJulia"); Pkg.precompile()'


# Copy the start script into the container
COPY binder/start /usr/local/bin/start
RUN chmod +x /usr/local/bin/start

# Expose the port Pluto will run on
EXPOSE 1234

# Run the start script when the container launches
CMD ["/usr/local/bin/start"]

