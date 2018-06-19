---

layout: default
---
<!-- Setting Use Case -->
<div class="environment-settings col-12" id="environment-settings">
<h2>Environment Settings</h2>
<hr />
<ol>
<li>
<h3>Login</h3>
</li>
<pre>
<code>
 - name: vCloudDirectorAnsible
   hosts: XXXXXXXXXXXX
   environment:
	env_user: XXXXXXXXXXXX
	env_password: XXXXXXXXXXXX
	env_host: XXXXXXXXXXXX
	env_org: XXXXXXXXXXXX
	env_api_version: XXXXXXXXXXXX
	env_verify_ssl_certs: XXXXXXXXXXXX

</code>
</pre>
<p>
VCD Ansible Modules prefer following two ways to set login variables for vCloud Director instance. 
</p>
<ol>
<li>
<b>Environment Variables - </b>
The end user can set login variables in the environment as shown above. Once they are set, modules will use these variables for all the subsequent resource operations automatically.
</li>
<li>
<b>Local Variables - </b>
The end user can set login variables for specific module(s) as local variables. This approach gives more freedom to the end user to execute specific module(s) on specific vCloud Director instance(s).
</li>
</ol>
<br />
<p>
By default, the priority will be given to <b>Local Variables</b> than <b>Environment Variables.</b>
</p>
<li>
<h3>Response</h3>
<p>VCD Ansible Modules provide a unanimous response. The response shall contain following properties,</p>
<ul>
<li>msg - the success/failure string corresponding to the resource</li>
<li>changed - "true" if resource has been modified at the infrastrucutre else "false"
</li>
</ul>
</li>
</ol>
</div>
<!--				  -->

<!-- Catalogs Use Case -->
<div class="catalog-usage col-12" id="catalog-usage">
<h2>Catalog Example Usage</h2>
<hr />
<ol>
<li>
<h3>Catalog States</h3>
<ul>
<li>
<h5>Create Catalog</h5>
</li>
<pre>
<code>
 - name: create catalog
   vcd_catalog:
	catalog_name: "test_catalog"
	description: "test_description"
	state: "present"

</code>
</pre>
 <h5>Argument Reference</h5>
 <ul>
<li>user - (Optional) - vCloud Director user name</li>
<li>password - (Optional) - vCloud Director password</li>
<li>org - (Optional) - vCloud Director org name to log into</li>
<li>host - (Optional) - vCloud Director host name</li>
<li>api_version - (Optional) - Pyvcloud API version</li>
<li>verify_ssl_certs - (Optional) - "true" to enforce to verify ssl certificate for each requests else "false"</li>
<li>catalog_name - (Required) Name of the catalog</li>
<li>description - (Required) Description Text for the catalog</li>
<li>state == "present" (Required) to create catalog</li>
</ul>
<li>
<h5>Update Catalog</h5>
</li>
<pre>
<code>
 - name: update catalog name and description
   vcd_catalog:
	catalog_name: "test_catalog" 
	new_catalog_name: "new_test_catalog" 
	description: "test_description"
	state: "update"
 </code>
 </pre>
 <h5>Argument Reference</h5>
 <ul>
 <li>user - (Optional) - vCloud Director user name</li>
 <li>password - (Optional) - vCloud Director password</li>
 <li>org - (Optional) - vCloud Director org name to log into</li>
 <li>host - (Optional) - vCloud Director host name</li>
 <li>api_version - (Optional) - Pyvcloud API version</li>
 <li>verify_ssl_certs - (Optional) - "true" to enforce to verify ssl certificate for each requests else "false"</li>
 <li>catalog_name - (Required) Old name of the catalog</li>
 <li>new_catalog_name - (Required) New name of the catalog</li>
 <li>description - (Required) New description text for the catalog</li>
 <li>state == "update" (Required) to update catalog</li>
 </ul>
 <li>
 <h5>Delete Catalog</h5>
 </li>
 <pre>
 <code>
 - name: delete catalog
   vcd_catalog:
	catalog_name: "test_catalog"
	state: "absent"
 </code>
 </pre>
 <h5>Argument Reference</h5>
 <ul>
 <li>user - (Optional) - vCloud Director user name</li>
 <li>password - (Optional) - vCloud Director password</li>
 <li>org - (Optional) - vCloud Director org name to log into</li>
 <li>host - (Optional) - vCloud Director host name</li>
 <li>api_version - (Optional) - Pyvcloud API version</li>
 <li>verify_ssl_certs - (Optional) - "true" to enforce to verify ssl certificate for each requests else "false"</li>
 <li>catalog_name - (Required) Name of the catalog</li>
 <li>state == "absent" (Required) to delete catalog</li>
 </ul>
 </ul>
</li>
 <li>
 <h3>Catalog Operations</h3>
 <ul>
 <li>
 <h5>Share/Unshare Catalog</h5>
 <pre>
 <code>
 - name: share/unshare catalog
   vcd_catalog:
	catalog_name: "test_catalog" 
	shared: "true"
	operation: "shared"
 </code>
 </pre>
 <h5>Argument Reference</h5>
 <ul>
 <li>user - (Optional) - vCloud Director user name</li>
 <li>password - (Optional) - vCloud Director password</li>
 <li>org - (Optional) - vCloud Director org name to log into</li>
 <li>host - (Optional) - vCloud Director host name</li>
 <li>api_version - (Optional) - Pyvcloud API version</li>
 <li>verify_ssl_certs - (Optional) - "true" to enforce to verify ssl certificate for each requests else "false"</li>
 <li>catalog_name - (Required) Name of the catalog</li>
 <li>shared - (Optional) "true"/"false" to share/unshare the catalog. The default value is "true" for the argument</li>
 <li>state == "operation" (Required) to share/unshare catalog</li>
</ul>
</li>
</ul>
</li>
</ol>
</div>
<!--				  -->

<!-- Catalog Item Use Case -->
<!--				  -->

<!-- vApp Use Case -->
<!--				  -->

<!-- vApp VM Use Case -->
<!--				  -->

<!-- Independent Disk Use Case -->
<div class="disk-usage col-12" id="disk-usage">
<h2>Disk Example Usage</h2>
<hr />
<ol>
<li>
<h3>Disk States</h3>
</li>
<ul>
<li>
<h5>Create Disk</h5>
</li>
<pre>
<code>
 - name: create disk
   vcd_disk:
	disk_name: "test_disk"
	description: "Test Disk"
	size: "100"
	vdc: "Test_VDC"
	state: "present"

</code>
</pre>
<h5>Argument Reference</h5>
<ul>
<li>user - (Optional) - vCloud Director user name</li>
<li>password - (Optional) - vCloud Director password</li>
<li>org - (Optional) - vCloud Director org name to log into</li>
<li>host - (Optional) - vCloud Director host name</li>
<li>api_version - (Optional) - Pyvcloud API version</li>
<li>verify_ssl_certs - (Optional) - "true" to enforce to verify ssl certificate for each requests else "false"</li>
<li>disk_name - (Required) name of the new disk</li>
<li>description - (Optional) description of the new disk</li>
<li>size - (Required) size of the disk in bytes</li>
<li>vdc - (Required) name of the virutal data center</li>
<li>bus_type - (Optional) bus type of the disk</li>
<li>bus_sub_type - (Optional) bus subtype of the disk</li>
<li>storage_profile_name - (Optional) name of an existing storage profile to be used by the new disk</li>
<li>iops - (Optional) iops requirement of the disk</li>
<li>state == "present" (Required) to create org</li>
</ul>
<li>
<h5>Update Disk</h5>
</li>
<pre>
<code>
 - name: update disk
   vcd_disk:
	disk_name: "test_disk"
	new_disk_name: "test_disk_1"
	new_size: "200"
	vdc: "Test_VDC"
	state: "update"

</code>
</pre>
<h5>Argument Reference</h5>
<ul>
<li>user - (Optional) - vCloud Director user name</li>
<li>password - (Optional) - vCloud Director password</li>
<li>org - (Optional) - vCloud Director org name to log into</li>
<li>host - (Optional) - vCloud Director host name</li>
<li>api_version - (Optional) - Pyvcloud API version</li>
<li>verify_ssl_certs - (Optional) - "true" to enforce to verify ssl certificate for each requests else "false"</li>
<li>disk_name - (Required) name of the existing disk</li>
<li>vdc - (Required) name of the virtual data center</li>
<li>disk_id - (Optional) id of the existing disk</li>
<li>new_disk_name - (Optional) new name of the disk</li>
<li>new_size - (Optional) new size of the disk</li>
<li>new_description - (Optional) new description of the disk</li>
<li>new_storage_profile_name - (Optional) new storage profile that the disk will be moved to</li>
<li>new_iops - (Optional) new iops requirement of the disk</li>
<li>state == "update" (Required) to update org</li>
</ul>
<li>
<h5>Delete Disk</h5>
</li>
<pre>
<code>
 - name: delete disk
   vcd_disk:
	disk_name: "test_disk"
	vdc: "Test_VDC"
	state: "absent"

</code>
</pre>
<h5>Argument Reference</h5>
<ul>
<li>user - (Optional) - vCloud Director user name</li>
<li>password - (Optional) - vCloud Director password</li>
<li>org - (Optional) - vCloud Director org name to log into</li>
<li>host - (Optional) - vCloud Director host name</li>
<li>api_version - (Optional) - Pyvcloud API version</li>
<li>verify_ssl_certs - (Optional) - "true" to enforce to verify ssl certificate for each requests else "false"</li>
<li>disk_name - (Required) name of the disk to delete</li>
<li>disk_id - (Optional) id of the disk to delete</li>
<li>vdc - (Required) name of the virtual datacenter</li>
<li>state == "absent" (Required) to create org</li>
</ul>
</ul>
</ol>
</div>
<!--				  -->

<!-- Org Use Case -->
<div class="org-usage col-12" id="org-usage">
<h2>Org Example Usage</h2>
<hr />
<ol>
 <li>
 <h3>Org States</h3>
 </li>
 <ul>
 <li>
 <h5>Create Org</h5>
 </li>
 <pre>
 <code>
 - name: create org
   vcd_org:
	org_name: "test_org"
	full_name: "test_org"
	is_enabled : "false"
	state: "present"
 </code>
</pre>
<h5>Argument Reference</h5>
<ul>
<li>user - (Optional) - vCloud Director user name</li>
<li>password - (Optional) - vCloud Director password</li>
<li>org - (Optional) - vCloud Director org name to log into</li>
<li>host - (Optional) - vCloud Director host name</li>
<li>api_version - (Optional) - Pyvcloud API version</li>
<li>verify_ssl_certs - (Optional) - "true" to enforce to verify ssl certificate for each requests else "false"</li>
<li>org_name - (Required) name of the organization</li>
<li>full_name - (Required) full name of the organization</li>
<li>is_enabled - (Optional) enable organization if True. The default value is False</li>
<li>state == "present" (Required) to create org</li>
</ul>
<li>
<h5>Update Org</h5>
</li>
<pre>
<code>
 - name: update org
   vcd_org:
	org_name: "test_org"
	is_enabled: "true"
	state: "update"

</code>
</pre>
<h5>Argument Reference</h5>
<ul>
<li>user - (Optional) - vCloud Director user name</li>
<li>password - (Optional) - vCloud Director password</li>
<li>org - (Optional) - vCloud Director org name to log into</li>
<li>host - (Optional) - vCloud Director host name</li>
<li>api_version - (Optional) - Pyvcloud API version</li>
<li>verify_ssl_certs - (Optional) - "true" to enforce to verify ssl certificate for each requests else "false"</li>
<li>org_name - (Required) name of the organization</li>
<li>is_enabled - (Optional) enable organization if True. The default value is None</li>
<li>state == "update" (Required) to update org</li>
</ul>
<li>
<h5>Delete Org</h5>
</li>
<pre>
<code>
 - name: delete org
   vcd_org:
	org_name: "test_org"
	force: "true"
	recursive: "true"
	state: "absent"

</code>
</pre>
<h5>Argument Reference</h5>
<ul>
<li>user - (Optional) - vCloud Director user name</li>
<li>password - (Optional) - vCloud Director password</li>
<li>org - (Optional) - vCloud Director org name to log into</li>
<li>host - (Optional) - vCloud Director host name</li>
<li>api_version - (Optional) - Pyvcloud API version</li>
<li>verify_ssl_certs - (Optional) - "true" to enforce to verify ssl certificate for each requests else "false"</li>
<li>org_name - (Required) name of the organization</li>
<li>force - (Optional) force=True along with recursive=True to remove
an organization and any objects it contains, regardless of their state</li>
<li>recursive - (Optional) recursive=True to remove an organization
and any objects it contains that are in a state that normally allows removal</li>
<li>state == "absent" (Required) to delete org</li>
</ul>
</ul>
<li>
<h3>Org Operations</h3>
</li>
<ul>
<li>
<h5>Read Org</h5>
</li>
<pre>
<code>
 - name: read org
   vcd_org:
	org_name: "test_org"
	operation: "read"

</code>
</pre>
<h5>Argument Reference</h5>
<ul>
<li>user - (Optional) - vCloud Director user name</li>
<li>password - (Optional) - vCloud Director password</li>
<li>org - (Optional) - vCloud Director org name to log into</li>
<li>host - (Optional) - vCloud Director host name</li>
<li>api_version - (Optional) - Pyvcloud API version</li>
<li>verify_ssl_certs - (Optional) - "true" to enforce to verify ssl certificate for each requests else "false"</li>
<li>org_name - (Required) name of the organization</li>
<li>operation == "read" (Required) to read organization</li>
</ul>
</ul>
</ol>
</div>
<!--				  -->

<!-- Org VDC Use Case -->
<!--				  -->

<!-- User Use Case -->
<div class="user-usage col-12" id="user-usage">
<h2>User Example Usage</h2>
 <hr />
 <ol>
 <li>
 <h3>User States</h3>
 </li>
 <ul>
 <li>
 <h5>Create User</h5>
 </li>
 <pre>
 <code>
 - name: create user
   vcd_user:
	username: "test_user"
	userpassword: test_password
	role_name: "Organization Administrator"
	full_username: "test_admin_user"
	description: "admin test user"
	email: "testuser@test.com"
	telephone: "12345678"
	im: "i_m_val"
	is_enabled: "false"
	stored_vm_quota: 5
	deployed_vm_quota: 5
	is_alert_enabled: "true"
	is_external: "false"
	is_default_cached: "false"
	is_group_role: "false"
	alert_email_prefix: "test"
	alert_email: "test@test.com"
	state: "present"
 </code>
 </pre>
 <h5>Argument Reference</h5>
 <ul>
 <li>user - (Optional) - vCloud Director user name</li>
 <li>password - (Optional) - vCloud Director password</li>
 <li>org - (Optional) - vCloud Director org name to log into</li>
 <li>host - (Optional) - vCloud Director host name</li>
 <li>api_version - (Optional) - Pyvcloud API version</li>
 <li>verify_ssl_certs - (Optional) - "true" to enforce to verify ssl certificate for each requests else "false"</li>
 <li>username - (Required) The username of the user</li>
 <li>userpassword - (Required) The password of the user (must be at least 6
 characters long)</li>
 <li>role_name - (Required) User role name</li>
 <li>full_username - (Required) The full name of the user</li>
 <li>description - (Required) The description for the User</li>
 <li>email - (Required) The email of the user</li>
 <li>telephone - (Required) The telephone of the user</li>
 <li>im - (Required) The im address of the user</li>
 <li>is_enabled - (Required) "true"/"false" Enable user</li>
 <li>stored_vm_quota - (Required) The quota of vApps that this user can store</li>
 <li>deployed_vm_quota - (Required) The quota of vApps that this user can deploy concurrently</li>
 <li>is_alert_enabled - (Required) "true"/"false" The alert email address</li>
 <li>is_external - (Required) "true"/"false" Indicates if user is imported from an external source</li>
 <li>is_default_cached - (Required) "true"/"false" Indicates if user should be cached</li>
 <li>is_group_role - (Required) "true"/"false" Indicates if the user has a group role</li>
 <li>alert_email_prefix - (Required) The string to prepend to the alert message subject line</li>
 <li>alert_email - (Required) The alert email address</li>
 <li>state == "present" (Required) to create user</li>
</ul>
<li>
<h5>Update User</h5>
</li>
<pre>
 <code>
 - name: update user
   vcd_user:
	username: "test_user"
	is_enabled: "true"
	state: "update"
 </code>
</pre>
<h5>Argument Reference</h5>
 <ul>
 <li>user - (Optional) - vCloud Director user name</li>
 <li>password - (Optional) - vCloud Director password</li>
 <li>org - (Optional) - vCloud Director org name to log into</li>
 <li>host - (Optional) - vCloud Director host name</li>
 <li>api_version - (Optional) - Pyvcloud API version</li>
 <li>verify_ssl_certs - (Optional) - "true" to enforce to verify ssl certificate for each requests else "false"</li>
 <li>username - (Required) username of the user</li>
 <li>is_enabled - (Required) "true"/"false" enable/disable the user</li>
 <li>state == "update" (Required) to update user</li>
</ul>
<li>
<h5>Delete User</h5>
</li>
<pre>
 <code>
 - name: delete user
   vcd_user:
	username: "test_user"
	state: "absent"
 </code>
</pre>
<h5>Argument Reference</h5>
 <ul>
 <li>user - (Optional) - vCloud Director user name</li>
 <li>password - (Optional) - vCloud Director password</li>
 <li>org - (Optional) - vCloud Director org name to log into</li>
 <li>host - (Optional) - vCloud Director host name</li>
 <li>api_version - (Optional) - Pyvcloud API version</li>
 <li>verify_ssl_certs - (Optional) - "true" to enforce to verify ssl certificate for each requests else "false"</li>
 <li>username - (Required) username of the user</li>
 <li>state == "absent" (Required) to update user</li>
</ul>
<!--				  -->