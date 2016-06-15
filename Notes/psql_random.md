If you want to copy stuff out of a local db:
* First do this, <code>Copy (Select * From foo) To '/tmp/test.csv' With CSV DELIMITER ',';</code>
* Then do this, <code>mv /tmp/test.csv ~/Desktop</code>
