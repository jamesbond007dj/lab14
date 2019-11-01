CREATE TABLE bookshelves ( id SERIAL PRIMARY KEY, name VARCHAR(255) );
-- 1. create a bookshelves table with id and name
INSERT INTO bookshelves(name) SELECT DISTINCT bookshelf FROM books;

ALTER TABLE books ADD COLUMN bookshelf_id INT;
-- 3: alter the books table to include a field for bookself_id

UPDATE books SET bookshelf_id=shelf.id FROM (SELECT * FROM bookshelves) AS shelf WHERE books.bookshelf = shelf.name;

ALTER TABLE books DROP COLUMN bookshelf;
-- 5: alter the books table to delete bookshelf column