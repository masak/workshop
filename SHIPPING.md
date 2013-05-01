Build a small DSL, with syntax something like this:

    shipment {
        from  "Hong Kong";
        to    "London";
        cargo "sand";
        date  "2013-07-03";
        days  10;
    }

Make a program that processes this kind of code, makes sure that "from" and
"to" are specified, gives the rest of the values sensible defaults, and outputs
all of the shipments nicely.

Extra bonus points if you make it an (awesome) error for the inner "keywords"
to be called outside of `shipment`.

**«** [Previous](dsl.md) **|**
