Design Guidelines
=============

This project should be made as modular as possible – e.g. as a Theme and a Plugin, so that it could be easily applied to another WP project.


####1. Types of Views####


Should be made as an exportable Theme.

There are 5 view types:

1) Front page view: design/frontpage.psd

2) Search results view - when something is found: design/search-results.psd

3) Search results view - when nothing is found or on empty search: design/search-results-found-none.psd

4) Post view - for each category: e.g. design/mission-post-view.psd or design/user-agent-view.psd

5) User's public page and category view (showing all posts in category): design/list-user-category.psd


Pages are accessible via SEO-friendly URLs such as

http://website.name/post_name_slug


except for User and Category pages, which can have the standard WP SEO-friendly URLs, such as http://website.name/category/category_name



####2. Structure of the Design####

Should be made as an exportable Theme.

There will be 4 categories of posts:

- Agents

- Missions

- Agencies

- Practices

There may be more categories added later. The names of categories may change.

Every post in every category may be connected to another post in another category using Posts 2 Posts WP plugin - https://github.com/scribu/wp-posts-to-posts.

A modification of this plugin is required to make it possible to add a description of the connection, which could then be shown to the user if the setting to show the types of connections is switched on (the setting to show/hide connection description should be added into plugin).
(see design/agency-post-view.psd).

If the post has a text inside, it's shown under the header of the post, above the connections list. If not – nothing is shown (see design/agency-post-view.psd).

Themes should be responsive - that is, adjust to the width. However, the left and top margins are fixed as in design. There should always be the same distance to the right side of screen also if it's too narrow.

All names of all categories and their according headers on pages should be modifiable (e.g. "Agents" can be changed to "Users", "mission" can be changed to "project")

When the posts of the category are shown on a Page that lists linked posts, the category header is shown above them (shows the name of category, so modifiable)

The header of each post shows a prefix, which relates to category (e.g. on Agent category post called "Johnco" we can choose to show its name as "Johnco" or as "agent Johnco")

All posts can be linked to each other. So, for example, adding a post in Agents category user can link that post to 2 other posts in the Missions category, to 3 posts from the Agencies category, and to 1 post from Practices category.

These links will then be shown on the Post's view as demonstrated in design.

The actual authors pages (user pages listing all the author's posts) as well as the category's pages and tag's pages (listing all posts in category or with the tag) simply list all the posts as shown in the list-user-category.psd view.

Clicking any post leads to its page.

Every post has contacts fields, which have the actual Label (e.g. "website") and Content (e.g. "www.noduslabs.com"). Only the label is shown on the post's page, clicking on the label, opens a new window with the link.

Every contact field should also have attached a "type" of contact field when editing it, so the software "knows" that it's a Skype contact or Facebook link or Twitter, etc - for future use.

Every contact information is saved on the page as microformats vCard format. Clicking on vcard: header exports the vCard with contacts of the Agent/Mission/Practice/Agency to the user's computer.

If a phone number is clicked, it's opened in Skype:. If a mail is clicked it's open with mailto: in a new window.



####3. Search Behavior####

Should be integrated into the theme.

When the user performs empty search OR when nothing is found, a special page search-results-found-none is shown, which automatically gets the content of README.md of this repository http://github.com/noduslabs/specialagency highlighting with bold the headers marked with hashtags.
Above this text it shows a link + that leads to Signup/Login page and export of GitHub Star and Fork buttons from this repository using http://ghbtns.com/ plugin.

The search itself is performed by post names and tags. The results are shown as on the search-results.psd view.

Clicking on search results leads to according Posts.


####4. JSON Export####

Should be made as a WP Plugin.

Note: here we use the word "Node" to talk about "Posts", and "Edges" or "Connections" as the connections between the posts made using WP plugin.

Every page has an extension link that's accessible using "/json" or "/gexf" which exports all the Posts and Connections as a json or gexf format respectively.

Samples of these formats are available in xml/json_sample.json and xml/gexf_sample.gexf folder.

The logic of the export is

1) The Nodes are the posts (with their internal WP as  the Id and the name of the post as the Label. For example, the post of Agency category will be itself a node that's connected to all the Missions, Agents, and Practices, which will be also nodes. They, in turn, also all have connections to each other, which will be exported.

2) The Edges all get unique ID of the connection made using WP plugin as the Edge ID. The Source value is the Id of the Post (node) from which the link was made, the Target value is the Id of the node to which the connection was made. The edge_context value is ID of the user who created the connection. The statement_id is the name of the blog.

Therefore, for example, if you reach http://website.name/post_name/json you will see a JSON that exports all the connections of that posts to other posts and their connections between each other.

There should be 6 extra views:

1) http://website.name/post_name/json/without will only show connections between the posts connected to the main one, WITHOUT that main one.

2) http://website.name/post_name/json/showall will show the actual node, all the nodes connected to it, as well as the nodes that are connected to those nodes (2nd level connections)

3) http://website.name/post_name/json/showallextra will show the actual node, all the nodes connected to it, as well as the nodes that are connected to those nodes (2nd level connections) and the connections between those nodes

4) http://website.name/post_name/json/showallwithout same as 2) but without the main node 1

5) A view from the main page as in http://website.name/json or http://website.name/gexf exports all the nodes and all the connections between them.

6) A view from category or user page follows the same logic as 1,2,3 e.g. http:/website.name/category/category_name/showall will export all listed posts as nodes, and the nodes that are connected to them



