This is a simple test case for https://www.drupal.org/project/migrate_plus/issues/3322342

Later, I expanded it to cover setting URL aliases, see `my_path` in the JSON file and in the migration file.

1. Create a taxonomy vocabulary named "Product" (machine name: product). Add a term to it named "Test product".

2. Create a taxonomy vocabulary named "Office name" (machine name: office_name). Add a term to it named "Top level term".

3. Add a term reference field to the "Office name" vocabulary. Give it the name "Product" (machine name: field_product) and make it for terms of the product type.

4. Create a content type named "Entry" (machine name: entry).

5. Add a term reference to Entry named "Section" (machine name: field_section).

6. Edit the file migrations/migrate_nodes.yml in this module and change two of the numbers as follows:

`source:
  constants:
    pseudo_field_district_tid: [[SET THIS TO THE TID FOR "Top level term"]]
    product_term_tid: [[SET THIS TO THE TID FOR "Test product"]]
`

7. Visit admin/config/search/path/patterns and create a pathauto pattern. Set Entry nodes to use it.

8. In the root of the site, run this:

drush migrate-reset migrate_nodes_test && drush migrate-rollback migrate_nodes_test && drush migrate-import migrate_nodes_test
