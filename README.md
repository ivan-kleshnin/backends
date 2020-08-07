# High-level backend development is an open-problem

There are multiple approaches to develop a backend/API to your Web or Mobile app nowadays.
My goal here is to structure and categorize them to hopefully get a more precise picture
on what is going on here.

In 2020 there's no obvious way to approach API building. Like in 2012 it was still believed by many
that REST can be implemented "correctly" to "solve all our problems". It couldn't be further
from the truth but there was a hope at least. Not anymore. Twitter, Facebook, Netflix, Google and many
other teams tried-and-discarded the idea of REST layers/hierarchy as something worthy.

One of the key ideas of REST (documentation should be somehow tied to data) was correct and viable but approached 
from an entirely wrong angle. Bloating your HTTP with unrequested links and metadata, from the present, 
looks almost insane. This was solved by GraphQL (among other key points) in kinda the opposite way to what was originally proposed
by Roy Fielding. GraphL is a drop-in REST replacemend with mostly pros and no cons.

But many other questions remain and new ones keep emerging. "The perfect API" now looks less achievable then ever 
despite all the collective effort of scientists, engineers and all the other people.

