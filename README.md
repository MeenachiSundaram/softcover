# softcover

Out of the box softcover container is up and running.

## What is Softcover?

Softcover is a new publishing platform based on the production system and business model used by the Ruby on Rails Tutorial by Michael Hartl. Using Softcover, authors can build multi-format ebooks (HTML, EPUB, MOBI, and PDF) from common source files, optionally bundle them with media like screencast videos, and publish them to Softcover’s integrated sales platform with a single command.

## How to use this Image

### Create a Sample book

```
# docker run -v /your/path:/softcover -d meenachisundaram/softcover softcover new my_sample_book
```

- In **/your/path** new *my_sample_book* folder is created.
- By following the instruction in [softcover.io](http://manual.softcover.io/book) manual edit your sample book.

### Launch Softcover server

- Now launch a softcover server using the following command.

**Note:** Run this command inside the **my_sample_book** directory or **your_existing_book** directory.

```
# docker run --name mysoftcover -v "$PWD":/softcover -p 4000:4000 -d meenachisundaram/softcover softcover server
```

- Change the port value as per your requirement.
- Name of the container given is `mysoftcover`
- By visiting the webpage(http://ip:4000 or http://localhost:4000) we can see the preview of the book.
- Now whatever edit done in **/your/path/my_sample_book** or **/your/path/your_existing_book** will be automatically updated in http://ip:4000 or http://localhost:4000.

### Set up temporary ENV variables

```
# export mysoftcover="docker exec mysoftcover softcover"
```

- For standard convention I'm using `mysoftcover` name of the running container.
- Now all command similar to [softcover.io](http://manual.softcover.io/book) can be run by simply adding **$mysoftcover** infront of softcover.
- Example:
  - # $mysoftcover version
  - # $mysoftcover help
  - # $mysoftcover build:pdf
  - # $mysoftcover build:all

### Build books

- Now all types of book can be build using `build:all` command.

```
# $mysoftcover build:all
```

- All builded ebooks can be found in `"$PWD"/ebooks` directory.
