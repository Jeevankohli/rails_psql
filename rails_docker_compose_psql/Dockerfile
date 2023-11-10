
# Use the official Ruby image as the base image
FROM ruby:3.2.0

# Set the working directory in the container
WORKDIR /rails

# Install essential dependencies
RUN apt-get update -qq && \
    apt-get install -y build-essential libvips bash bash-completion libffi-dev tzdata postgresql nodejs npm yarn && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /usr/share/doc /usr/share/man

# Install Rails
RUN gem install rails

# Copy the Gemfile and Gemfile.lock into the container
COPY Gemfile Gemfile.lock ./

# Install gems
RUN bundle install

# Copy the application code into the container
COPY . .

# Expose port 3000 to the Docker network
EXPOSE 3000

# Start the Rails server
CMD ["rails", "server", "-b", "0.0.0.0"]
