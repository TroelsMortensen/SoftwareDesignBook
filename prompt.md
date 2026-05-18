Let's go with the first recommendation, add a new section after "Step 1: Start with the appliation layer".

Don't talk about hexagonal architecture here, this has not yet been introduced, and the reader my not understand the reference, unless that reference is to say something else will be introduced later.

Your definition is good, for the sublayer, let's keep that.

We must talk about dependencies within the application layer, and it's sublayers.

Good idea to contrast with entities or dtos modules.

The classic example, that this arose from is this: I have a CustomerService, which does stuff about customers. There is an OrderServices too. One day a developer adds a new feature to the CustomerService, like "View a customer with order history", so they realize they can use functionality already in the OrderService. Later on, another feature, now it's about viewing a specific order, but it includes customer information, so they realize they can use functionality already in the CustomerService. They make the OrderService depend on the CustomerService. Now we have a circular dependency. The point of the sub-layer is to prevent this kind of dependency from happening, by extracting the functionality into a separate sub-layer.
However, I need another example, which is in line with the Abyssal Watch case study for the book.

Other times, a sub-layer is because of some functionality which really doesn't fit into a standard Service class.
I would need a example for this also.

Don't move into DDD yet, or Domain Services. Don't put the domain inside application. 

The Sibling packages you mention can make sense, assembler and factory, for example.

I need to add a new package layout example. However, the current examples in this chapter uses the old diagram style. See the @hexagonal.tex file for the new style.

Let's skip code examples for now, and keep it theoretical.

Good with trade-offs.

Form a plan for including this into the chapter.