Produce highlighting for this fragment of Java code. First as regexes, then as
a grammar. The exercise is meant for you to be able to compare and contrast
these two approaches.

Perl 5 people can use Regexp::Grammars, Perl 6 people can use the built-in
grammars.

The highlighter takes a piece of code, like this:

    class HelloWorldApp {
        public static void main(String[] args) {
            System.out.println("Hello World!"); // Display the string.
        }
    }

And it produces a highlighted version, like this:

    \hlkeyword{class} \hlusertype{HelloWorldApp} \{
        \hlkeyword{public} \hlkeyword{static} \hlkeyword{void} main(\hlusertype{String}[] args) \{
            \hlusertype{System}.out.println(\hlliteral{"Hello World!"}); \hlcomment{// Display the string.}
        \}
    \}

In other words,

* Curly braces `{ }` are escaped: `\{ \}`
* Keywords, such as `class`, `public`, `static`, and `void` get highlighted as such
* Strings and numbers get highlighted as literals
* Comments get highlighted as comments
* Perhaps the trickiest one: non-primitive types get highlighted as such

Here are a few more example inputs with their corresponding highlighted output:

    class MountainBike extends Bicycle {
        // new fields and methods defining 
        // a mountain bike would go here
    }

    \hlkeyword{class} \hlusertype{MountainBike} \hlkeyword{extends} \hlusertype{Bicycle} \{
        \hlcomment{// new fields and methods defining}
        \hlcomment{// a mountain bike would go here}
    \}

    public interface List <E> {
        void add(E x);
        Iterator<E> iterator();
    }

    \hlkeyword{public} \hlkeyword{interface} \hlusertype{List} <\hlusertype{E}> \{
        \hlkeyword{void} add(\hlusertype{E} x);
        \hlusertype{Iterator}<\hlusertype{E}> iterator();
    \}

Extra kudos points if you actually hook this up to Latex and make it emit
highlighted source code.
