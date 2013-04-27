Implement a converter that takes an integer and renders that number in the
Roman numeral system.

For example, given the number 3, your converter should produce "III".

Here's a test to get you started:

    use Test::More tests => 1;
    
    is to_roman(3), "III", "3 gets converted to III";
