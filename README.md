This is a simple test case for https://www.drupal.org/project/migrate_plus/issues/3322342

1. Create a taxonomy vocabulary named "Section" (machine name: section).

2. Create a content type named "Entry" (machine name: entry).

3. Add a term reference to Entry named "Section" (machine name: field_section).

4. In the root of the site, run this:
drush migrate-rollback migrate_nodes_test && drush migrate-reset migrate_nodes_test && drush migrate-import migrate_nodes_test
