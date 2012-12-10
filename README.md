**[SNMP](http://www.wikipedia.org/wiki/SNMP) builder** is a add-in for [Zabbix](http://www.zabbix.com/) monitoring solution. It's visual (web [GUI](http://en.wikipedia.org/wiki/Graphical_user_interface)) [OID](http://en.wikipedia.org/wiki/Object_identifier) tree browser for direct creating of [Zabbix template items](http://www.zabbix.com/documentation/1.8/manual/config/items).

SNMPbuilder version is equal to Zabbix version for that it works.

Project's addres, help / docs, to-do: <https://github.com/cernekj/snmpbuilder>

Features
--------
- MIB Browser: It shows system's and your own's MIBs. Click on the tree to retrieve value and information about a OID. Click to select the OID as Zabbix's item.
- OID Table support: It assumes that a OID whose name's end with string 'Table' is a OID Table. OID Table will retrieve with all it's indexes. Click on the cell to select the index as Zabbix's item.
- Column selection: On OID Table, click on a header will select a whole column as Zabbix's items. It's useful if you create SNMP template for a 48 ports switch 8-).
- Auto convert: I implement a simple convert from SNMP Type to Zabbix's item.


Dependencies
------------
- [Net-SNMP package](http://www.net-snmp.org/)
- [Zabbix](http://www.zabbix.com/) v1.8
- [PHP](http://www.php.org/) v5.2


Installation
------------

I try my best to not patch Zabbix's code, but still did a little to integrate the tool into Zabbix.

- Unzip `snmp_builder.zip` into zabbix's web root. There is a `snmp_builder.php` and 3 js files under `snmp_builder` sub-dir.

- Open `snmp_builder.php`, edit `MIBS_ALL_PATH` for your own SNMP MIB's directories.

		define('MIBS_ALL_PATH', '/home/zabbix/public_html/snmp_builder/mibs:/usr/share/snmp/mibs');

- Open `include/menu.inc.php`. At line 203, insert a piece of code

		array('url'=>'snmp_builder.php',
				'label'=>'SNMP Builder'
			),

  Like this:

				'label'=>S_NOTIFICATIONS
			),
		array('url'=>'locales.php',
				'label'=>S_LOCALES
			),
		array('url'=>'snmp_builder.php',
				'label'=>'SNMP Builder'
			),
		array('url'=>'instal.php',
				'label'=>S_INSTALLATION,
				'sub_pages'=>array('setup.php','warning.php')
			)
		)

  It integrates `snmp_builder.php` as a menu item under Administration tab between Locales and Install menu. In fact, you can add it in any place.

- Open Zabbix, select Administration tab, you should see SNMP Builder in menu.

License
-------
[GNU GPLv2](http://www.gnu.org/licenses/old-licenses/gpl-2.0.html)


Authors
-------
- [giapnguyen](https://github.com/giapnguyen) – February 2010
- [J. Cernek](http://jakub.cernek.cz/) – December 2012


Alternatives
------------
- [zload_snmpwalk](http://zabbix.com/wiki/howto/monitor/snmp/zload_snmpwalk) – CLI only
