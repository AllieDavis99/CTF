# Mini-ject

Opening the Mini-ject website, we can immediately see a post that contains the SQL schema used to create the posts. 

```
      create table posts (
			  postid int,
			  private bool,
			  text varchar(1000),
			  author varchar(255)
			);
```

We see that the 'posts' table has a 'private' variable that should hide certain posts. We want to un-hide those posts.
We'll need to use an SQL injection to bypass the check that a post is private. 
It seems like the SQL SELECT statement being used only looks at whether a post is private and whether a post contains the string entered by the user. 
So the statement will take the form of either: 

```
SELECT * FROM posts WHERE posts.text contains {filter_text} AND posts.private = 'false'; 
```
or

```
SELECT * FROM posts WHERE posts.private = 'false' AND posts.text contains {filter_text};
```

The first statement is simpler to test because displaying the private posts only requires that we comment out the rest of the line, so we'll test that first. 
We can test this by entering the text:

```
";#
```
into the filter.
And sure enough, we see the post with the flag!

"You found a secret flag! osu{youweresupposedtodestroytheinjectnotjointhem}"
