
  Documentation
=====================
### t\_scope\_id ###
t\_scope\_id is a type which consists two string constat values as following:
- "local"
- "global"

```javascript
      /*          
      * t_scope_id is a type which consists two string constat values as following:
      * - "local"
      * - "global"
      */
      t_scope_id:and(
        /*
         * s
         */
        string(),
        or(
          equals( << 'local'  >>  ),
          equals( << 'global' >>  ),
        )
      ),
```

### t\_valuable\_id ###
t\_valuable\_id is a type of id which is used to specify
a "valuable". In Thankspedia.js, a valuable could be
a valuable thing such as a currency, a trading card
or other valuable materials.

```javascript
      /*          
      * t_valuable_id is a type of id which is used to specify
      * a "valuable". In Thankspedia.js, a valuable could be
      * a valuable thing such as a currency, a trading card
      * or other valuable materials.
      */
      t_valuable_id:uuid(),
```

### t\_valuable\_script ###
t\_valuable\_script is an ID which indicates the function of a valuable.
The possible values of t\_valuable\_script is currently following:

- check
- valuable

When the value is "check", the valuable is check as the meaning of banking
system. In that case, the valuable must specify other properties such as
drawee or owner of the valuable.

When the value is "valuable", currently it is always a currency. In future,
it is exntended to other materials such as drawings or trading cards.

```javascript
      /*          
      * t_valuable_script is an ID which indicates the function of a valuable.
      * The possible values of t_valuable_script is currently following:
      *
      * - check
      * - valuable
      *
      * When the value is "check", the valuable is check as the meaning of banking
      * system. In that case, the valuable must specify other properties such as
      * drawee or owner of the valuable.
      *
      * When the value is "valuable", currently it is always a currency. In future,
      * it is exntended to other materials such as drawings or trading cards.
      */
      t_valuable_script:string(),
```

### t\_timeline\_id ###
t\_timeline\_id is an ID which specifies a timeline in the Thankspedia.js
system. A timeline could be a timeline which is visible to a group and
shared in order to exchange messages; a timeline could also be a
notification message queue.

```javascript
      /*          
      * t_timeline_id is an ID which specifies a timeline in the Thankspedia.js
      * system. A timeline could be a timeline which is visible to a group and
      * shared in order to exchange messages; a timeline could also be a
      * notification message queue.
      */
      t_timeline_id:uuid(),
```

### t\_timelinename ###
t\_timelinename is a human readable ID which specifies a timeline. This ID
is specifically used to specify timelines in relative manner. The possible
values are following:

- global\_public\_output\_timeline
- global\_public\_input\_timeline
- global\_public\_notify\_timeline
- global\_private\_output\_timeline
- global\_private\_input\_timeline
- global\_private\_notify\_timeline
- local\_public\_output\_timeline
- local\_public\_input\_timeline
- local\_public\_notify\_timeline
- local\_private\_output\_timeline
- local\_private\_input\_timeline
- local\_private\_notify\_timeline

```javascript
      /*          
      * t_timelinename is a human readable ID which specifies a timeline. This ID
      * is specifically used to specify timelines in relative manner. The possible
      * values are following:
      *
      * - global_public_output_timeline
      * - global_public_input_timeline
      * - global_public_notify_timeline
      * - global_private_output_timeline
      * - global_private_input_timeline
      * - global_private_notify_timeline
      * - local_public_output_timeline
      * - local_public_input_timeline
      * - local_public_notify_timeline
      * - local_private_output_timeline
      * - local_private_input_timeline
      * - local_private_notify_timeline
      *
      */
      t_timelinename:string(),
```

### t\_profile\_id ###
t\_profile\_id is a type of IDs which specify profiles.  Note that In
`Thankspedia.js` a user can hold multiple profiles; a profile is always
attached to a timeline; and a timeline is always attached to a user. And A
user has multiple timelines.

For further information, see the tBC database definition.

```javascript
      /*          
      * t_profile_id is a type of IDs which specify profiles.  Note that In
      * `Thankspedia.js` a user can hold multiple profiles; a profile is always
      * attached to a timeline; and a timeline is always attached to a user. And A
      * user has multiple timelines.
      *
      * For further information, see the tBC database definition.
      */
      t_profile_id:uuid(),
```

### t\_has\_profile\_id ###
The type `t\_has\_profile\_id` guarantees that the specified object has
`profile\_id` property and its value is a proper value which is denoted
by the type `t\_profile\_id`.

```javascript
      /*          
      * The type `t_has_profile_id` guarantees that the specified object has
      * `profile_id` property and its value is a proper value which is denoted
      * by the type `t_profile_id`.
      */
      t_has_profile_id:object(
        profile_id : t_profile_id(),
      )

```

### t\_username\_or\_user\_id ###
t\_username\_or\_user\_id is a utility type which indicates the object has
either `user\_id` or `username`.

```javascript
      /*          
      * t_username_or_user_id is a utility type which indicates the object has
      * either `user_id` or `username`.
      */
      t_username_or_user_id:or(
        object(
          user_id : t_user_id(),
        ),
        object(
          username : t_username(),
        ),
      )

```

### t\_tbl\_user\_member\_timelines ###
t\_tbl\_user\_member\_timelines is a type which represents a row record
of the table `user\_member\_timelines`.

```javascript
      /*          
      * t_tbl_user_member_timelines is a type which represents a row record
      * of the table `user_member_timelines`.
      */
      t_tbl_user_member_timelines:object(
        user_id        : t_user_id(),
        member_user_id : t_user_id(),
        timelinename   : string(),
        timeline_id    : t_timeline_id(),
      )

```

### t\_tbl\_user\_timelines ###
t\_tbl\_user\_timelines is a type which represetns a row record
of the table `user\_timelines`.

```javascript
      /*          
      * t_tbl_user_timelines is a type which represetns a row record
      * of the table `user_timelines`.
      */
      t_tbl_user_timelines:object(
        user_id        : t_user_id(),
        timelinename   : string(),
        timeline_id    : t_timeline_id(),
      )

```

### t\_message\_template\_id ###
t\_message\_template\_id is an enumeration type. A value of
t\_message\_template\_id is indicates one of the predefined template
messages. These template messages are usually used in notification
timelines.

```javascript
      /*          
      * t_message_template_id is an enumeration type. A value of
      * t_message_template_id is indicates one of the predefined template
      * messages. These template messages are usually used in notification
      * timelines.
      */
      t_message_template_id:or(
        equals( << "message_test"               >>  ),
        equals( << "message_sent_valuables"     >>  ),
        equals( << "message_received_valuables" >>  ),
        equals( << "message_offered_valuables"  >>  ),
        equals( << "message_acquired_valuables" >>  ),
        equals( << "message_got_valuables"      >>  ),
        equals( << "message_mentioned"          >>  ),
        equals( << "message_liked"              >>  ),
        equals( << "message_reacted"            >>  ),
        equals( << "message_replied"            >>  ),
        equals( << "message_unknown"            >>  ),
        equals( << "message_error"              >>  ),
      )

```

### t\_message\_json ###
t\_message\_json is a type which represents the data formats of the
arguments which are applied to each predefined templatem message.

```javascript
      /*          
      * t_message_json is a type which represents the data formats of the
      * arguments which are applied to each predefined templatem message.
      */
      t_message_json:object(
        /*
         * - message_template_id: the message id to be shown in the timeline.
         * - subject_user: information of the user who sent the message.
         * - target_user: information of the user who is sent the message.
         * - message_template_id: a row record of the sent valuable.
         */
        message_template_id : t_message_template_id(),
        subject_user : object(),
        target_user : object(),
        valuable : t_tbl_valuable(),
      ),
```

### t\_read\_accounts\_mode ###
t\_read\_accounts\_mode is an enumeration type which specifies
the mode when a user calls read\_accounts() method.

See read\_accounts()

```javascript
      /*          
      * t_read_accounts_mode is an enumeration type which specifies
      * the mode when a user calls read_accounts() method.
      *
      * See read_accounts()
      */
      t_read_accounts_mode:and(
        string(),
        or(
          equals( << 'parents'  >>  ),
          equals( << 'children' >>  ),
          equals( << 'accounts'  >>  ),
        )
      ),
```

## get\_intl\_message

get\_intl\_message method retrieves a string value from a JSON object which
is stored in database. The JSON object contains all string data which are
necessary for internationalization.

### t\_typesafety\_input\_of\_get\_intl\_message ###

```javascript
      t_typesafety_input_of_get_intl_message:array(
        or(
          object(
            path    : array_of( string() ),
            lang_id : or( string(), null() ),
          ),
        )
      )
```

### t\_typesafety\_output\_of\_get\_intl\_message ###

```javascript
      t_typesafety_output_of_get_intl_message:any()

```

## get\_intl\_messages

get\_intl\_message method retrieves an object which contains data
for internationalization. There is a JSON object stored in the remote server
and it contains all information which is necessary for internationalization.
This `get\_intl\_messages` returns its entire object.

### t\_typesafety\_input\_of\_get\_intl\_messages ###
lang\_id: Specify a language id or null to retrieve all.

```javascript
      /*          
      * lang_id: Specify a language id or null to retrieve all.
      */
      t_typesafety_input_of_get_intl_messages:array(
        object(
          lang_id : or( string(), null() ),
        ),
      )
```

### t\_typesafety\_output\_of\_get\_intl\_messages ###
Return Value: JSON object contains the data for internationalization.

```javascript
      /*          
      * Return Value: JSON object contains the data for internationalization.
      */
      t_typesafety_output_of_get_intl_messages:any()

```

## get\_available\_intl\_messages

get\_available\_intl\_messages() returns all available IDs which can be
specified as `lang\_id` of get\_intl\_messages/get\_intl\_message API.

### t\_typesafety\_input\_of\_get\_available\_intl\_messages ###

```javascript
      t_typesafety_input_of_get_available_intl_messages:array( string() )
```

### t\_typesafety\_output\_of\_get\_available\_intl\_messages ###

```javascript
      t_typesafety_output_of_get_available_intl_messages:array_of( any() )
```

## create\_or\_update\_user

The create\_or\_update\_user API method let you create or update a user data.
In order to use this API method  properly, it is important to understand
the relationable table structure of Thankspedia tBC's database. For further information,
please see Appendix.

### t\_typesafety\_input\_of\_create\_or\_update\_user ###
#### Parameters
user: specifies a user to create or update

```javascript
      /*          
      * #### Parameters
      * user: specifies a user to create or update
      */
      t_typesafety_input_of_create_or_update_user:nargs(
        user : object(
          username : string(),
        ),
      )

```

### t\_typesafety\_output\_of\_create\_or\_update\_user ###

```javascript
      t_typesafety_output_of_create_or_update_user:object(
        user : object(
          username : string(),
        ),
      ),
```

## delete\_user

The delete\_user  API method let you delete a user data.
In order to use this API method  properly, it is important to understand
the relationable table structure of Thankspedia tBC's database. For further information,
please see Appendix.

### t\_typesafety\_input\_of\_delete\_user ###
#### Parameters
user: specifies a user to delete.

```javascript
      /*          
      * #### Parameters
      * user: specifies a user to delete.
      */
      t_typesafety_input_of_delete_user:nargs(
        user : t_username_or_user_id(),
      )

```

### t\_typesafety\_output\_of\_delete\_user ###

```javascript
      t_typesafety_output_of_delete_user:object(
        user : object(
          user_id  : t_user_id(),
          username : t_username(),
        ),
      ),
```

## delete\_multiple\_users

delete\_multiple\_users allows you to delete multiple users at once.

### t\_typesafety\_input\_of\_delete\_multiple\_users ###
#### Parameters
- users: an array contains objects of the users to be deleted

```javascript
      /*          
      * #### Parameters
      * - users: an array contains objects of the users to be deleted
      */
      t_typesafety_input_of_delete_multiple_users:nargs()

```

### t\_typesafety\_output\_of\_delete\_multiple\_users ###

```javascript
      t_typesafety_output_of_delete_multiple_users:any()

```

## has\_user

has\_user returns true when the specified user does exist. The user is to
be specified as user\_id.

### t\_typesafety\_input\_of\_has\_user ###

```javascript
      /*          
      *
      */
      t_typesafety_input_of_has_user:nargs()

```

### t\_typesafety\_output\_of\_has\_user ###

```javascript
      t_typesafety_output_of_has_user:any()

```

## has\_username

has\_user returns true when the specified user does exist. The user is to be
specified by username.

### t\_typesafety\_input\_of\_has\_username ###

```javascript
      t_typesafety_input_of_has_username:nargs()

```

### t\_typesafety\_output\_of\_has\_username ###

```javascript
      t_typesafety_output_of_has_username:any()

```

## read\_user

read\_user API method returns an object contains data of a user.

### t\_typesafety\_input\_of\_read\_user ###
#### Parameter:
- user: information of the specified user

```javascript
      /*          
      * #### Parameter:
      * - user: information of the specified user
      */
      t_typesafety_input_of_read_user:nargs()

```

### t\_typesafety\_output\_of\_read\_user ###
#### Return Value:
- Information of the specified user

```javascript
      /*          
      * #### Return Value:
      * - Information of the specified user
      *
      */
      t_typesafety_output_of_read_user:object(
        user : or(
          object(
            user_id :t_user_id() ,
          ),
          object(
            username : t_username(),
          ),
          null(),
        )
      )

```

## user\_id2username

user\_id2username() API method returns username of a specified user which
is specified by a user\_id.

### t\_typesafety\_input\_of\_user\_id2username ###
#### Parameter:
- user\_id: user\_id to be converted to username

```javascript
      /*          
      * #### Parameter:
      * - user_id: user_id to be converted to username
      */
      t_typesafety_input_of_user_id2username:nargs()

```

### t\_typesafety\_output\_of\_user\_id2username ###

```javascript
      t_typesafety_output_of_user_id2username:any()

```

## username2user\_id

username2user\_id() API method returns user\_id of a specified user which
is specified by a username.

### t\_typesafety\_input\_of\_username2user\_id ###
#### Parameter
- username: username to be converted to user\_id

```javascript
      /*          
      * #### Parameter
      * - username: username to be converted to user_id
      *
      */
      t_typesafety_input_of_username2user_id:nargs(
        username : t_username(),
      )

```

### t\_typesafety\_output\_of\_username2user\_id ###

```javascript
      t_typesafety_output_of_username2user_id:object(
        user_id: t_user_id(),
      )

```

## read\_all\_users

read\_all\_users API method returns data records of all users

### t\_typesafety\_input\_of\_read\_all\_users ###

```javascript
      t_typesafety_input_of_read_all_users:nargs()

```

### t\_typesafety\_output\_of\_read\_all\_users ###

```javascript
      t_typesafety_output_of_read_all_users:any()

```

## count\_all\_users

count\_all\_users API method returns the number of all users

### t\_typesafety\_input\_of\_count\_all\_users ###

```javascript
      t_typesafety_input_of_count_all_users:nargs()

```

### t\_typesafety\_output\_of\_count\_all\_users ###

```javascript
      t_typesafety_output_of_count_all_users:any()

```

## create\_or\_update\_user\_authentication

create\_or\_update\_user\_authentication API method creates or update
authentication information of a user. In this system, a record of a user
information can be related to a record of authentication information. When
a record of a user is not related to a record of authentication information,
the user is not allowed to be logged in.

For further information about tBC's database table structure, see Appendix.

### t\_typesafety\_input\_of\_create\_or\_update\_user\_authentication ###

```javascript
      t_typesafety_input_of_create_or_update_user_authentication:nargs()

```

### t\_typesafety\_output\_of\_create\_or\_update\_user\_authentication ###

```javascript
      t_typesafety_output_of_create_or_update_user_authentication:any()

```

## update\_user\_authentication

update\_user\_authentication API method updates the record of authentication information.
This method is deprecated and not used anymore.

### t\_typesafety\_input\_of\_update\_user\_authentication ###

```javascript
      t_typesafety_input_of_update_user_authentication:nargs()

```

### t\_typesafety\_output\_of\_update\_user\_authentication ###

```javascript
      t_typesafety_output_of_update_user_authentication:any()

```

## read\_user\_authentication

read\_user\_authentication API method reads a record of authentication
information of a user and return it.

### t\_typesafety\_input\_of\_read\_user\_authentication ###

```javascript
      t_typesafety_input_of_read_user_authentication:nargs()

```

### t\_typesafety\_output\_of\_read\_user\_authentication ###

```javascript
      t_typesafety_output_of_read_user_authentication:any()

```

## delete\_user\_authentication

delete\_user\_authentication API method deletes a record of authentication
information of the specified user.

### t\_typesafety\_input\_of\_delete\_user\_authentication ###

```javascript
      t_typesafety_input_of_delete_user_authentication:nargs()

```

### t\_typesafety\_output\_of\_delete\_user\_authentication ###

```javascript
      t_typesafety_output_of_delete_user_authentication:any()

```

## read\_all\_user\_authentications

read\_all\_user\_authentications API method reads all records of all users and
returns them as an array. This method is deprecated and not used anymore.

### t\_typesafety\_input\_of\_read\_all\_user\_authentications ###

```javascript
      t_typesafety_input_of_read_all_user_authentications:nargs()

```

### t\_typesafety\_output\_of\_read\_all\_user\_authentications ###

```javascript
      t_typesafety_output_of_read_all_user_authentications:any()

```

## get\_parent\_users

get\_parent\_users API method retrieves all related parent users of a
specified user.

### t\_typesafety\_input\_of\_get\_parent\_users ###

```javascript
      t_typesafety_input_of_get_parent_users:nargs()

```

### t\_typesafety\_output\_of\_get\_parent\_users ###

```javascript
      t_typesafety_output_of_get_parent_users:any()

```

## get\_wallet\_contents

get\_wallet\_contents API method returns each number of all valuables which
are belonged to a specified user.

### t\_typesafety\_input\_of\_get\_wallet\_contents ###

```javascript
      t_typesafety_input_of_get_wallet_contents:fold_right(
        or(
          object(
            username : t_username(),
          ),
          object(
            user_id  : t_user_id(),
          )
        )
      ),
```

### t\_typesafety\_output\_of\_get\_wallet\_contents ###

```javascript
      t_typesafety_output_of_get_wallet_contents:array_of(
        object(
          wallet_id   : uuid(),
          valuable_id : uuid(),
          valuable_name : string(),
          current_valuable_quantity : string(),
        )
      )

```

## abstract\_login

`abstract\_login` is not an API method but a virtual method which is
required to be defined by `authentication-context`. It defines the processes
how the system authenticates users and the conditions which users are allowed to be
logged in.

## abstract\_login\_information

get\_wallet\_contents is an API method which returns each number of all
valuables which are belonged to a specified user.

### t\_typesafety\_input\_of\_abstract\_login\_information ###

```javascript
      t_typesafety_input_of_abstract_login_information:array(t_user_identity_token())
```

### t\_typesafety\_output\_of\_abstract\_login\_information ###

```javascript
      t_typesafety_output_of_abstract_login_information:t_user_login_info()
```

## abstract\_switch\_current\_user

get\_wallet\_contents is not an API method but a virtual method which is
required to be defined by `authentication-context` module. It defines how
the system authorizes a user to switch to other users.

### t\_typesafety\_input\_of\_abstract\_switch\_current\_user ###

```javascript
      t_typesafety_input_of_abstract_switch_current_user:nargs()

```

### t\_typesafety\_output\_of\_abstract\_switch\_current\_user ###

```javascript
      t_typesafety_output_of_abstract_switch_current_user:boolean()
```

## read\_user\_member

read\_user\_member API method returns records of specified member users.

### t\_typesafety\_input\_of\_read\_user\_member ###

```javascript
      t_typesafety_input_of_read_user_member:nargs()

```

### t\_typesafety\_output\_of\_read\_user\_member ###

```javascript
      t_typesafety_output_of_read_user_member:any()

```

## var\_ensure\_user\_id

var\_ensure\_user\_id is not an API method but an utilizy method. When
var\_ensure\_user\_id receives a username value as a field of an object, it
creates the corresponding user\_id value as a field of the received object.

### t\_typesafety\_input\_of\_var\_ensure\_user\_id ###

```javascript
      t_typesafety_input_of_var_ensure_user_id:array(
        or(
          object(
            user_id : uuid(),
          ),
          object(
            username : string(),
          ),
        )
      )
```

### t\_typesafety\_output\_of\_var\_ensure\_user\_id ###

```javascript
      t_typesafety_output_of_var_ensure_user_id:object(
        user_id  : or( t_user_id(),  null()      ),
        username : or( t_username(), undefined() ),
      )

```

## var\_ensure\_member\_user\_id

### t\_typesafety\_input\_of\_var\_ensure\_member\_user\_id ###

```javascript
      t_typesafety_input_of_var_ensure_member_user_id:array(
        or(
          object(
            member_user_id  : uuid(),
          ),
          object(
            member_username : string(),
          ),
        )
      )

```

### t\_typesafety\_output\_of\_var\_ensure\_member\_user\_id ###

```javascript
      t_typesafety_output_of_var_ensure_member_user_id:object(
        member_user_id  : or( t_user_id(), null() ),
        member_username : or( t_username(), undefined() ),
      )

```

## create\_or\_update\_user\_member

### t\_typesafety\_input\_of\_create\_or\_update\_user\_member ###

```javascript
      t_typesafety_input_of_create_or_update_user_member:nargs()

```

### t\_typesafety\_output\_of\_create\_or\_update\_user\_member ###

```javascript
      t_typesafety_output_of_create_or_update_user_member:any()

```

## delete\_user\_member

### t\_typesafety\_input\_of\_delete\_user\_member ###

```javascript
      t_typesafety_input_of_delete_user_member:nargs()

```

### t\_typesafety\_output\_of\_delete\_user\_member ###

```javascript
      t_typesafety_output_of_delete_user_member:any()

```

## delete\_multiple\_user\_members

### t\_typesafety\_input\_of\_delete\_multiple\_user\_members ###

```javascript
      t_typesafety_input_of_delete_multiple_user_members:nargs()

```

### t\_typesafety\_output\_of\_delete\_multiple\_user\_members ###

```javascript
      t_typesafety_output_of_delete_multiple_user_members:any()

```

## read\_filtered\_user\_members

### t\_typesafety\_input\_of\_read\_filtered\_user\_members ###

```javascript
      t_typesafety_input_of_read_filtered_user_members:nargs()

```

### t\_typesafety\_output\_of\_read\_filtered\_user\_members ###

```javascript
      t_typesafety_output_of_read_filtered_user_members:any()

```

## read\_accounts

### t\_typesafety\_input\_of\_read\_accounts ###

```javascript
      t_typesafety_input_of_read_accounts:nargs(
        username : or( t_username(), null() ),
        mode     : or( t_read_accounts_mode(), null() ),
      )

```

### t\_typesafety\_output\_of\_read\_accounts ###

```javascript
      t_typesafety_output_of_read_accounts:any()

```

## create\_or\_update\_account

### t\_typesafety\_input\_of\_create\_or\_update\_account ###

```javascript
      t_typesafety_input_of_create_or_update_account:nargs()

```

### t\_typesafety\_output\_of\_create\_or\_update\_account ###

```javascript
      t_typesafety_output_of_create_or_update_account:any()

```

## create\_or\_update\_accounts

### t\_typesafety\_input\_of\_create\_or\_update\_accounts ###

```javascript
      t_typesafety_input_of_create_or_update_accounts:nargs()

```

### t\_typesafety\_output\_of\_create\_or\_update\_accounts ###

```javascript
      t_typesafety_output_of_create_or_update_accounts:any()

```

## create\_message

### t\_typesafety\_input\_of\_create\_message ###

```javascript
      t_typesafety_input_of_create_message:nargs()

```

### t\_typesafety\_output\_of\_create\_message ###

```javascript
      t_typesafety_output_of_create_message:any()

```

## write\_message

### t\_typesafety\_input\_of\_write\_message ###

```javascript
      t_typesafety_input_of_write_message:nargs()

```

### t\_typesafety\_output\_of\_write\_message ###

```javascript
      t_typesafety_output_of_write_message:any()

```

## read\_message

### t\_typesafety\_input\_of\_read\_message ###

```javascript
      t_typesafety_input_of_read_message:nargs()

```

### t\_typesafety\_output\_of\_read\_message ###

```javascript
      t_typesafety_output_of_read_message:any()

```

## delete\_message

### t\_typesafety\_input\_of\_delete\_message ###

```javascript
      t_typesafety_input_of_delete_message:nargs()

```

### t\_typesafety\_output\_of\_delete\_message ###

```javascript
      t_typesafety_output_of_delete_message:any()

```

## test\_stored\_procedure

### t\_typesafety\_input\_of\_test\_stored\_procedure ###

```javascript
      t_typesafety_input_of_test_stored_procedure:nargs()

```

### t\_typesafety\_output\_of\_test\_stored\_procedure ###

```javascript
      t_typesafety_output_of_test_stored_procedure:any()

```

## create\_timeline

### t\_typesafety\_input\_of\_create\_timeline ###

```javascript
      t_typesafety_input_of_create_timeline:nargs(
        timeline : or(
          object(),
          object(
            timeline_id : uuid(),
          ),
        ),
      )

```

### t\_typesafety\_output\_of\_create\_timeline ###

```javascript
      t_typesafety_output_of_create_timeline:any()

```

## read\_timeline

### t\_typesafety\_input\_of\_read\_timeline ###

```javascript
      t_typesafety_input_of_read_timeline:nargs()

```

### t\_typesafety\_output\_of\_read\_timeline ###

```javascript
      t_typesafety_output_of_read_timeline:any()

```

## delete\_timeline

### t\_typesafety\_input\_of\_delete\_timeline ###

```javascript
      t_typesafety_input_of_delete_timeline:nargs()

```

### t\_typesafety\_output\_of\_delete\_timeline ###

```javascript
      t_typesafety_output_of_delete_timeline:any()

```

## read\_view\_timeline\_and\_profile

### t\_typesafety\_input\_of\_read\_view\_timeline\_and\_profile ###

```javascript
      t_typesafety_input_of_read_view_timeline_and_profile:nargs()

```

### t\_typesafety\_output\_of\_read\_view\_timeline\_and\_profile ###

```javascript
      t_typesafety_output_of_read_view_timeline_and_profile:any()

```

## create\_or\_update\_view\_user\_and\_user\_timeline\_and\_timeline\_and\_profile

### t\_typesafety\_input\_of\_create\_or\_update\_view\_user\_and\_user\_timeline\_and\_timeline\_and\_profile ###

```javascript
      t_typesafety_input_of_create_or_update_view_user_and_user_timeline_and_timeline_and_profile:fold_right(
        and(
          t_username_or_user_id(),
          object(
            timeline_id :
              or(
                t_timeline_id(),
                null(),
                undefined(),
              )
          )
        ),
      )

```

### t\_typesafety\_output\_of\_create\_or\_update\_view\_user\_and\_user\_timeline\_and\_timeline\_and\_profile ###

```javascript
      t_typesafety_output_of_create_or_update_view_user_and_user_timeline_and_timeline_and_profile:any()

```

## create\_or\_update\_view\_user\_member\_and\_user\_timeline\_and\_timeline\_and\_profile

### t\_typesafety\_input\_of\_create\_or\_update\_view\_user\_member\_and\_user\_timeline\_and\_timeline\_and\_profile ###

```javascript
      t_typesafety_input_of_create_or_update_view_user_member_and_user_timeline_and_timeline_and_profile:nargs()

```

### t\_typesafety\_output\_of\_create\_or\_update\_view\_user\_member\_and\_user\_timeline\_and\_timeline\_and\_profile ###

```javascript
      t_typesafety_output_of_create_or_update_view_user_member_and_user_timeline_and_timeline_and_profile:any()

```

## read\_view\_users\_and\_user\_timeline\_and\_timeline\_and\_profile

### t\_typesafety\_input\_of\_read\_view\_users\_and\_user\_timeline\_and\_timeline\_and\_profile ###

```javascript
      t_typesafety_input_of_read_view_users_and_user_timeline_and_timeline_and_profile:nargs()

```

### t\_typesafety\_output\_of\_read\_view\_users\_and\_user\_timeline\_and\_timeline\_and\_profile ###

```javascript
      t_typesafety_output_of_read_view_users_and_user_timeline_and_timeline_and_profile:any()

```

## read\_view\_user\_member\_and\_user\_timeline\_and\_timeline\_and\_profile

### t\_typesafety\_input\_of\_read\_view\_user\_member\_and\_user\_timeline\_and\_timeline\_and\_profile ###

```javascript
      t_typesafety_input_of_read_view_user_member_and_user_timeline_and_timeline_and_profile:nargs()

```

### t\_typesafety\_output\_of\_read\_view\_user\_member\_and\_user\_timeline\_and\_timeline\_and\_profile ###

```javascript
      t_typesafety_output_of_read_view_user_member_and_user_timeline_and_timeline_and_profile:any()

```

## user\_timelines\_to\_object

### t\_typesafety\_input\_of\_user\_timelines\_to\_object ###

```javascript
      t_typesafety_input_of_user_timelines_to_object:nargs()

```

### t\_typesafety\_output\_of\_user\_timelines\_to\_object ###

```javascript
      t_typesafety_output_of_user_timelines_to_object:any()

```

## object\_to\_user\_timelines

### t\_typesafety\_input\_of\_object\_to\_user\_timelines ###

```javascript
      t_typesafety_input_of_object_to_user_timelines:nargs()

```

### t\_typesafety\_output\_of\_object\_to\_user\_timelines ###

```javascript
      t_typesafety_output_of_object_to_user_timelines:any()

```

## create\_or\_update\_profile

### t\_typesafety\_input\_of\_create\_or\_update\_profile ###

```javascript
      t_typesafety_input_of_create_or_update_profile:nargs()

```

### t\_typesafety\_output\_of\_create\_or\_update\_profile ###

```javascript
      t_typesafety_output_of_create_or_update_profile:any()

```

## read\_profile

### t\_typesafety\_input\_of\_read\_profile ###

```javascript
      t_typesafety_input_of_read_profile:nargs()

```

### t\_typesafety\_output\_of\_read\_profile ###

```javascript
      t_typesafety_output_of_read_profile:any()

```

## delete\_profile

### t\_typesafety\_input\_of\_delete\_profile ###

```javascript
      t_typesafety_input_of_delete_profile:nargs()

```

### t\_typesafety\_output\_of\_delete\_profile ###

```javascript
      t_typesafety_output_of_delete_profile:any()

```

## create\_timeline\_content

### t\_typesafety\_input\_of\_create\_timeline\_content ###

```javascript
      t_typesafety_input_of_create_timeline_content:nargs()

```

### t\_typesafety\_output\_of\_create\_timeline\_content ###

```javascript
      t_typesafety_output_of_create_timeline_content:any()

```

## read\_timeline\_content

### t\_typesafety\_input\_of\_read\_timeline\_content ###

```javascript
      t_typesafety_input_of_read_timeline_content:nargs()

```

### t\_typesafety\_output\_of\_read\_timeline\_content ###

```javascript
      t_typesafety_output_of_read_timeline_content:any()

```

## delete\_timeline\_content

### t\_typesafety\_input\_of\_delete\_timeline\_content ###

```javascript
      t_typesafety_input_of_delete_timeline_content:nargs()

```

### t\_typesafety\_output\_of\_delete\_timeline\_content ###

```javascript
      t_typesafety_output_of_delete_timeline_content:any()

```

## is\_timeline\_following

### t\_typesafety\_input\_of\_is\_timeline\_following ###

```javascript
      t_typesafety_input_of_is_timeline_following:nargs()

```

### t\_typesafety\_output\_of\_is\_timeline\_following ###

```javascript
      t_typesafety_output_of_is_timeline_following:any()

```

## follow\_timeline

### t\_typesafety\_input\_of\_follow\_timeline ###

```javascript
      t_typesafety_input_of_follow_timeline:nargs()

```

### t\_typesafety\_output\_of\_follow\_timeline ###

```javascript
      t_typesafety_output_of_follow_timeline:any()

```

## unfollow\_timeline

### t\_typesafety\_input\_of\_unfollow\_timeline ###

```javascript
      t_typesafety_input_of_unfollow_timeline:nargs()

```

### t\_typesafety\_output\_of\_unfollow\_timeline ###

```javascript
      t_typesafety_output_of_unfollow_timeline:any()

```

## create\_or\_update\_valuable

### t\_typesafety\_input\_of\_create\_or\_update\_valuable ###

```javascript
      t_typesafety_input_of_create_or_update_valuable:nargs()

```

### t\_typesafety\_output\_of\_create\_or\_update\_valuable ###

```javascript
      t_typesafety_output_of_create_or_update_valuable:any()

```

## create\_valuable

### t\_typesafety\_input\_of\_create\_valuable ###

```javascript
      t_typesafety_input_of_create_valuable:nargs()

```

### t\_typesafety\_output\_of\_create\_valuable ###

```javascript
      t_typesafety_output_of_create_valuable:any()

```

## update\_valuable

### t\_typesafety\_input\_of\_update\_valuable ###

```javascript
      t_typesafety_input_of_update_valuable:nargs()

```

### t\_typesafety\_output\_of\_update\_valuable ###

```javascript
      t_typesafety_output_of_update_valuable:any()

```

## disableValuable

### t\_typesafety\_input\_of\_disableValuable ###

```javascript
      t_typesafety_input_of_disableValuable:nargs()

```

### t\_typesafety\_output\_of\_disableValuable ###

```javascript
      t_typesafety_output_of_disableValuable:any()

```

## read\_valuable

### t\_typesafety\_input\_of\_read\_valuable ###

```javascript
      t_typesafety_input_of_read_valuable:nargs()

```

### t\_typesafety\_output\_of\_read\_valuable ###

```javascript
      t_typesafety_output_of_read_valuable:any()

```

## delete\_valuable

### t\_typesafety\_input\_of\_delete\_valuable ###

```javascript
      t_typesafety_input_of_delete_valuable:nargs()

```

### t\_typesafety\_output\_of\_delete\_valuable ###

```javascript
      t_typesafety_output_of_delete_valuable:any()

```

## read\_all\_valuables

### t\_typesafety\_input\_of\_read\_all\_valuables ###

```javascript
      t_typesafety_input_of_read_all_valuables:nargs()

```

### t\_typesafety\_output\_of\_read\_all\_valuables ###

```javascript
      t_typesafety_output_of_read_all_valuables:any()

```

## issue\_valuables

### t\_typesafety\_input\_of\_issue\_valuables ###

```javascript
      t_typesafety_input_of_issue_valuables:nargs()

```

### t\_typesafety\_output\_of\_issue\_valuables ###

```javascript
      t_typesafety_output_of_issue_valuables:any()

```

## update\_valuable\_state

### t\_typesafety\_input\_of\_update\_valuable\_state ###

```javascript
      t_typesafety_input_of_update_valuable_state:array(
        object(
          valuable_id      : uuid(),
          valuable_enabled : boolean(),
        )
      )
```

### t\_typesafety\_output\_of\_update\_valuable\_state ###

```javascript
      t_typesafety_output_of_update_valuable_state:any()

```

## download\_valuable\_state

### t\_typesafety\_input\_of\_download\_valuable\_state ###

```javascript
      t_typesafety_input_of_download_valuable_state:array(
        object(
          valuable_id      : uuid(),
        )
      )

```

### t\_typesafety\_output\_of\_download\_valuable\_state ###

```javascript
      t_typesafety_output_of_download_valuable_state:any()

```

## confiscate\_all\_valuable\_deposits

### t\_typesafety\_input\_of\_confiscate\_all\_valuable\_deposits ###

```javascript
      t_typesafety_input_of_confiscate_all_valuable_deposits:nargs()

```

### t\_typesafety\_output\_of\_confiscate\_all\_valuable\_deposits ###

```javascript
      t_typesafety_output_of_confiscate_all_valuable_deposits:any()

```

## create\_wallet

### t\_typesafety\_input\_of\_create\_wallet ###

```javascript
      t_typesafety_input_of_create_wallet:nargs()

```

### t\_typesafety\_output\_of\_create\_wallet ###

```javascript
      t_typesafety_output_of_create_wallet:any()

```

## update\_wallet

### t\_typesafety\_input\_of\_update\_wallet ###

```javascript
      t_typesafety_input_of_update_wallet:nargs()

```

### t\_typesafety\_output\_of\_update\_wallet ###

```javascript
      t_typesafety_output_of_update_wallet:any()

```

## disableWallet

### t\_typesafety\_input\_of\_disableWallet ###

```javascript
      t_typesafety_input_of_disableWallet:nargs()

```

### t\_typesafety\_output\_of\_disableWallet ###

```javascript
      t_typesafety_output_of_disableWallet:any()

```

## read\_wallet

### t\_typesafety\_input\_of\_read\_wallet ###

```javascript
      t_typesafety_input_of_read_wallet:nargs()

```

### t\_typesafety\_output\_of\_read\_wallet ###

```javascript
      t_typesafety_output_of_read_wallet:any()

```

## delete\_wallet

### t\_typesafety\_input\_of\_delete\_wallet ###

```javascript
      t_typesafety_input_of_delete_wallet:nargs()

```

### t\_typesafety\_output\_of\_delete\_wallet ###

```javascript
      t_typesafety_output_of_delete_wallet:any()

```

## request\_valuable\_transfer

### t\_typesafety\_input\_of\_request\_valuable\_transfer ###

```javascript
      t_typesafety_input_of_request_valuable_transfer:nargs()

```

### t\_typesafety\_output\_of\_request\_valuable\_transfer ###

```javascript
      t_typesafety_output_of_request_valuable_transfer:any()

```

## respond\_valuable\_transfer

### t\_typesafety\_input\_of\_respond\_valuable\_transfer ###

```javascript
      t_typesafety_input_of_respond_valuable_transfer:nargs()

```

### t\_typesafety\_output\_of\_respond\_valuable\_transfer ###

```javascript
      t_typesafety_output_of_respond_valuable_transfer:any()

```

## parse\_message\_commands

### t\_typesafety\_input\_of\_parse\_message\_commands ###

```javascript
      t_typesafety_input_of_parse_message_commands:array(
        object(
          message_text         : string(),
        )
      )
```

### t\_typesafety\_output\_of\_parse\_message\_commands ###

```javascript
      t_typesafety_output_of_parse_message_commands:object(
        statements : array_of(
          object(
            command_name : or(
              string(),
              null(),
            ),
            message_chunk_list : array_of(
              string(),
            ),
            target_valuables : array_of(
              object(
                valuable_name : string(),
                valuable_quantity : number(),
              ),
            ),
            target_users : array_of(
              object(
                username : string(),
              ),
            ),
            message : string(),
          ),
        ),
      )

```

## execute\_message\_commands

### t\_typesafety\_input\_of\_execute\_message\_commands ###

```javascript
      t_typesafety_input_of_execute_message_commands:fold_right(
        object(
          default_parent_user_id : t_user_id(),
          scope_id     : t_scope_id(),
          subject_user : object(
            user_id : t_user_id(),
          ),
          statements : array_of(
            object(
              command_name : or(
                string(),
                null(),
              ),
              message_chunk_list : array_of(
                string(),
              ),
              target_valuables : array_of(
                object(
                  valuable_name : string(),
                  valuable_quantity : number(),
                ),
              ),
              target_users : array_of(
                object(
                  username : or( string(), undefined() ),
                ),
              ),
              message : string(),
            ),
          ),
          message_id : or( uuid(), null() ),
        )
      )

```

### t\_typesafety\_output\_of\_execute\_message\_commands ###

```javascript
      t_typesafety_output_of_execute_message_commands:any(),
```

## get\_notify\_timeline\_from\_user

### t\_typesafety\_input\_of\_get\_notify\_timeline\_from\_user ###

```javascript
      t_typesafety_input_of_get_notify_timeline_from_user:nargs(
        scope_id : t_scope_id(),
        user_id  : t_user_id(),
      ),
```

### t\_typesafety\_output\_of\_get\_notify\_timeline\_from\_user ###

```javascript
      t_typesafety_output_of_get_notify_timeline_from_user:t_tbl_user_timelines(),
```

## get\_notify\_timeline\_from\_member\_user

### t\_typesafety\_input\_of\_get\_notify\_timeline\_from\_member\_user ###

```javascript
      t_typesafety_input_of_get_notify_timeline_from_member_user:nargs(
        scope_id : t_scope_id(),
        user_id  :t_user_id(),
        member_user_id : t_user_id(),
      ),
```

### t\_typesafety\_output\_of\_get\_notify\_timeline\_from\_member\_user ###

```javascript
      t_typesafety_output_of_get_notify_timeline_from_member_user:t_tbl_user_member_timelines(),
```

### t\_sndmsg\_user ###

```javascript
      t_sndmsg_user:or(
        and(
          or(
            object(
              username : string(),
            ),
            object(
              user_id  : uuid(),
            ),
          ),
          or(
            object(
              walletname : string(),
            ),
            object(
              wallet_id  : uuid(),
            ),
          ),
        ),
        and(
          or(
            object(
              username : string(),
            ),
            object(
              user_id  : uuid(),
            ),
          ),
          or(
            object(
              member_username : string(),
            ),
            object(
              member_user_id  : uuid(),
            ),
          ),
          or(
            object(
              walletname : string(),
            ),
            object(
              wallet_id  : uuid(),
            ),
          ),
        ),
      ),
```

### t\_tbl\_valuable ###

```javascript
      t_tbl_valuable:object(
        valuable_id              : uuid(),
        valuable_name            : string(),
        valuable_attrs           : object(),
        valuable_script          : or( string(), null() ),
        valuable_params          : object(),
        valuable_created_date    : any(),
        valuable_modified_date   : any(),
        valuable_expiration_date : any(),
        valuable_enabled         : boolean(),
      ),
```

### t\_sndmsg\_cmd\_base ###

```javascript
      t_sndmsg_cmd_base:object(
        default_parent_user_id : t_user_id(),
        scope_id               : t_scope_id(),
        subject_user  : object(
          user_id : t_user_id(),
          primary_wallet_id : uuid(),
        ),
        target_users      : array_of(
          object(
            primary_wallet_id : uuid(),
          )
        ),
        message_id        : or( uuid() , null() ),
      ),
```

### i\_sndmsg\_cmd2 ###

```javascript
      i_sndmsg_cmd2:object(
        valuable_id            : t_valuable_id(),
        valuable_quantity      : number(),
        valuable_script        : t_valuable_script(),
        valuable_attrs         : object(),
      ),
```

### i\_sndmsg\_cmd ###

```javascript
      i_sndmsg_cmd:object(
        valuable   : t_tbl_valuable(),
      ),
```

### t\_sndmsg\_cmd ###

```javascript
      t_sndmsg_cmd:and(
        i_sndmsg_cmd(),
        t_sndmsg_cmd_base(),
      ),
```

## sndmsg\_util\_transfer

### t\_typesafety\_input\_of\_sndmsg\_util\_transfer ###

```javascript
      t_typesafety_input_of_sndmsg_util_transfer:fold_right(
        object(
          valuable_id       : uuid(),
          valuable_quantity : number(),
          from_wallet_id    : uuid(),
          to_wallet_id      : uuid(),
          message_id        : or( uuid() , null() ),
        )
      )

```

### t\_typesafety\_output\_of\_sndmsg\_util\_transfer ###

```javascript
      t_typesafety_output_of_sndmsg_util_transfer:any()

```

## sndmsg\_util\_notification

### t\_typesafety\_input\_of\_sndmsg\_util\_notification ###

```javascript
      t_typesafety_input_of_sndmsg_util_notification:fold_right(
        object(
          scope_id               : t_scope_id(),
          default_parent_user_id : t_user_id(),
          user_id                : t_user_id(),
          target_user   : or( object(), null() ),
          subject_user  : or( object(), null() ),
          valuable      : or( object(), null() ),
        )
      ),
```

### t\_typesafety\_output\_of\_sndmsg\_util\_notification ###

```javascript
      t_typesafety_output_of_sndmsg_util_notification:undefined(),
```

## sndmsg\_cmd\_message

### t\_typesafety\_input\_of\_sndmsg\_cmd\_message ###

```javascript
      t_typesafety_input_of_sndmsg_cmd_message:fold_right(
        t_sndmsg_cmd_base()
      )

```

### t\_typesafety\_output\_of\_sndmsg\_cmd\_message ###

```javascript
      t_typesafety_output_of_sndmsg_cmd_message:any()

```

## sndmsg\_cmd\_check

### t\_typesafety\_input\_of\_sndmsg\_cmd\_check ###

```javascript
      t_typesafety_input_of_sndmsg_cmd_check:array(
        t_sndmsg_cmd(),
      )

```

### t\_typesafety\_output\_of\_sndmsg\_cmd\_check ###

```javascript
      t_typesafety_output_of_sndmsg_cmd_check:any()

```

## sndmsg\_cmd\_valuable

### t\_typesafety\_input\_of\_sndmsg\_cmd\_valuable ###

```javascript
      t_typesafety_input_of_sndmsg_cmd_valuable:fold_right(
        t_sndmsg_cmd(),
      )

```

### t\_typesafety\_output\_of\_sndmsg\_cmd\_valuable ###

```javascript
      t_typesafety_output_of_sndmsg_cmd_valuable:any()

```

## read\_valuable\_transactions

### t\_typesafety\_input\_of\_read\_valuable\_transactions ###

```javascript
      t_typesafety_input_of_read_valuable_transactions:nargs(
        valuable_id : uuid(),
        from : or( string(), null() ),
        to   : or( string(), null() ),
      )

```

### t\_typesafety\_output\_of\_read\_valuable\_transactions ###

```javascript
      t_typesafety_output_of_read_valuable_transactions:any()

```

## read\_valuable\_deposits

### t\_typesafety\_input\_of\_read\_valuable\_deposits ###

```javascript
      t_typesafety_input_of_read_valuable_deposits:nargs(
        valuable_id : uuid(),
      )

```

### t\_typesafety\_output\_of\_read\_valuable\_deposits ###

```javascript
      t_typesafety_output_of_read_valuable_deposits:any()

```

### t\_message\_content\_type ###

```javascript
      t_message_content_type:or(
        equals( << 'content_json' >>  ),
        equals( << 'content_text' >>  ),
      )

```

### t\_message\_text\_content\_text ###

```javascript
      t_message_text_content_text:string(),
```

### t\_message\_text\_content\_json ###

```javascript
      t_message_text_content_json:object(),
```

## send\_message

### t\_typesafety\_input\_of\_send\_message ###

```javascript
      t_typesafety_input_of_send_message:nargs(
        timeline_id          : or( t_timeline_id(), null() ),
        user_id              : or( t_user_id(), null() ),
        parent_message_id    : or( uuid(), null() ),
        message_content_type : t_message_content_type(),
        message_text         : or(
          t_message_text_content_text(),
          t_message_text_content_json(),
        )
      )

```

### t\_typesafety\_output\_of\_send\_message ###

```javascript
      t_typesafety_output_of_send_message:any()
```

## send\_tweet

### t\_typesafety\_input\_of\_send\_tweet ###

```javascript
      t_typesafety_input_of_send_tweet:nargs(
        user_id                : t_user_id(),
        scope_id               : t_scope_id(),
        default_parent_user_id : t_user_id(),
        parent_message_id      : or( uuid(), null() ),
        message_text           : string(),
        message_content_type   : or( null(), t_message_content_type() ),
      )

```

### t\_typesafety\_output\_of\_send\_tweet ###

```javascript
      t_typesafety_output_of_send_tweet:any()
```

## receive\_tweets

### t\_typesafety\_input\_of\_receive\_tweets ###

```javascript
      t_typesafety_input_of_receive_tweets:array(
        object(
          user_id     : or( null(), uuid() ),
          timeline_id : or( null(), uuid() ),
          mode        : or(
            equals( << 'newer' >>  ),
            equals( << 'older' >>  ),
          ),
          older_than  : or( null(), string() ),
          window_size : or( null(), number() ),
        )
      )
```

### t\_typesafety\_output\_of\_receive\_tweets ###

```javascript
      t_typesafety_output_of_receive_tweets:any()

```

## get\_locale\_message

### t\_typesafety\_input\_of\_get\_locale\_message ###

```javascript
      t_typesafety_input_of_get_locale_message:array_of(
        string()
      )

```

### t\_typesafety\_output\_of\_get\_locale\_message ###

```javascript
      t_typesafety_output_of_get_locale_message:any()

```

## get\_global\_common\_input\_timeline\_id

### t\_typesafety\_input\_of\_get\_global\_common\_input\_timeline\_id ###

```javascript
      t_typesafety_input_of_get_global_common_input_timeline_id:array()
```

### t\_typesafety\_output\_of\_get\_global\_common\_input\_timeline\_id ###

```javascript
      t_typesafety_output_of_get_global_common_input_timeline_id:uuid()
```

## create\_or\_update\_user\_timeline

### t\_typesafety\_input\_of\_create\_or\_update\_user\_timeline ###

```javascript
      t_typesafety_input_of_create_or_update_user_timeline:nargs(
        user_id : t_user_id(),
        timelinename : t_timelinename(),
        timeline_id : or(
          t_timeline_id(),
          null(),
          undefined(),
        )
      )

```

### t\_typesafety\_output\_of\_create\_or\_update\_user\_timeline ###

```javascript
      t_typesafety_output_of_create_or_update_user_timeline:object(
        timeline_id : t_timeline_id(),
      )

```

## read\_user\_timeline

### t\_typesafety\_input\_of\_read\_user\_timeline ###

```javascript
      t_typesafety_input_of_read_user_timeline:nargs()

```

### t\_typesafety\_output\_of\_read\_user\_timeline ###

```javascript
      t_typesafety_output_of_read_user_timeline:any()

```

## delete\_user\_timeline

### t\_typesafety\_input\_of\_delete\_user\_timeline ###

```javascript
      t_typesafety_input_of_delete_user_timeline:nargs()

```

### t\_typesafety\_output\_of\_delete\_user\_timeline ###

```javascript
      t_typesafety_output_of_delete_user_timeline:any()

```

## create\_or\_update\_user\_watching\_timeline

### t\_typesafety\_input\_of\_create\_or\_update\_user\_watching\_timeline ###

```javascript
      t_typesafety_input_of_create_or_update_user_watching_timeline:nargs()

```

### t\_typesafety\_output\_of\_create\_or\_update\_user\_watching\_timeline ###

```javascript
      t_typesafety_output_of_create_or_update_user_watching_timeline:any()

```

## read\_user\_watching\_timeline

### t\_typesafety\_input\_of\_read\_user\_watching\_timeline ###

```javascript
      t_typesafety_input_of_read_user_watching_timeline:nargs()

```

### t\_typesafety\_output\_of\_read\_user\_watching\_timeline ###

```javascript
      t_typesafety_output_of_read_user_watching_timeline:any()

```

## delete\_user\_watching\_timeline

### t\_typesafety\_input\_of\_delete\_user\_watching\_timeline ###

```javascript
      t_typesafety_input_of_delete_user_watching_timeline:nargs()

```

### t\_typesafety\_output\_of\_delete\_user\_watching\_timeline ###

```javascript
      t_typesafety_output_of_delete_user_watching_timeline:any()

```

## create\_or\_update\_user\_member\_timeline

### t\_typesafety\_input\_of\_create\_or\_update\_user\_member\_timeline ###

```javascript
      t_typesafety_input_of_create_or_update_user_member_timeline:nargs()

```

### t\_typesafety\_output\_of\_create\_or\_update\_user\_member\_timeline ###

```javascript
      t_typesafety_output_of_create_or_update_user_member_timeline:any()

```

## read\_user\_member\_timeline

### t\_typesafety\_input\_of\_read\_user\_member\_timeline ###

```javascript
      t_typesafety_input_of_read_user_member_timeline:fold_right(
        and(
          object(
            user_id        : t_user_id(),
            member_user_id : t_user_id(),
          ),
          or(
            object(
              timelinename : string(),
            ),
            object(
              timeline_id  : string(),
            ),
          ),
        ),
      ),
```

### t\_typesafety\_output\_of\_read\_user\_member\_timeline ###

```javascript
      t_typesafety_output_of_read_user_member_timeline:t_tbl_user_member_timelines()

```

## delete\_user\_member\_timeline

### t\_typesafety\_input\_of\_delete\_user\_member\_timeline ###

```javascript
      t_typesafety_input_of_delete_user_member_timeline:nargs()

```

### t\_typesafety\_output\_of\_delete\_user\_member\_timeline ###

```javascript
      t_typesafety_output_of_delete_user_member_timeline:any()

```

## create\_or\_update\_user\_member\_watching\_timeline

### t\_typesafety\_input\_of\_create\_or\_update\_user\_member\_watching\_timeline ###

```javascript
      t_typesafety_input_of_create_or_update_user_member_watching_timeline:nargs()

```

### t\_typesafety\_output\_of\_create\_or\_update\_user\_member\_watching\_timeline ###

```javascript
      t_typesafety_output_of_create_or_update_user_member_watching_timeline:any()

```

## read\_user\_member\_watching\_timeline

### t\_typesafety\_input\_of\_read\_user\_member\_watching\_timeline ###

```javascript
      t_typesafety_input_of_read_user_member_watching_timeline:nargs()

```

### t\_typesafety\_output\_of\_read\_user\_member\_watching\_timeline ###

```javascript
      t_typesafety_output_of_read_user_member_watching_timeline:any()

```

## delete\_user\_member\_watching\_timeline

### t\_typesafety\_input\_of\_delete\_user\_member\_watching\_timeline ###

```javascript
      t_typesafety_input_of_delete_user_member_watching_timeline:nargs()

```

### t\_typesafety\_output\_of\_delete\_user\_member\_watching\_timeline ###

```javascript
      t_typesafety_output_of_delete_user_member_watching_timeline:any()

```

## list\_child\_users

### t\_typesafety\_input\_of\_list\_child\_users ###

```javascript
      t_typesafety_input_of_list_child_users:nargs()

```

### t\_typesafety\_output\_of\_list\_child\_users ###

```javascript
      t_typesafety_output_of_list_child_users:any()

```

## get\_random\_user

### t\_typesafety\_input\_of\_get\_random\_user ###

```javascript
      t_typesafety_input_of_get_random_user:nargs()

```

### t\_typesafety\_output\_of\_get\_random\_user ###

```javascript
      t_typesafety_output_of_get_random_user:any()

```

## get\_random\_member\_user

### t\_typesafety\_input\_of\_get\_random\_member\_user ###

```javascript
      t_typesafety_input_of_get_random_member_user:nargs()

```

### t\_typesafety\_output\_of\_get\_random\_member\_user ###

```javascript
      t_typesafety_output_of_get_random_member_user:any()

```

## parse\_message\_text

### t\_typesafety\_input\_of\_parse\_message\_text ###

```javascript
      t_typesafety_input_of_parse_message_text:nargs()

```

### t\_typesafety\_output\_of\_parse\_message\_text ###

```javascript
      t_typesafety_output_of_parse_message_text:any()

```

## send\_random\_member\_user\_tweet

### t\_typesafety\_input\_of\_send\_random\_member\_user\_tweet ###

```javascript
      t_typesafety_input_of_send_random_member_user_tweet:nargs()

```

### t\_typesafety\_output\_of\_send\_random\_member\_user\_tweet ###

```javascript
      t_typesafety_output_of_send_random_member_user_tweet:any()

```

## send\_random\_user\_tweet

### t\_typesafety\_input\_of\_send\_random\_user\_tweet ###

```javascript
      t_typesafety_input_of_send_random_user_tweet:fold_right(
        object(
          user_id                : t_user_id(),
          scope_id               : t_scope_id(),
          default_parent_user_id : t_user_id(),
          parent_message_id      : or( uuid(), null() ),
          message_content_type   : t_message_content_type(),
        )
      )

```

### t\_typesafety\_output\_of\_send\_random\_user\_tweet ###

```javascript
      t_typesafety_output_of_send_random_user_tweet:any()

```

## test\_blob

### t\_typesafety\_input\_of\_test\_blob ###

```javascript
      t_typesafety_input_of_test_blob:nargs()

```

### t\_typesafety\_output\_of\_test\_blob ###

```javascript
      t_typesafety_output_of_test_blob:any()

```

## get\_default\_image

### t\_typesafety\_input\_of\_get\_default\_image ###

```javascript
      t_typesafety_input_of_get_default_image:nargs()

```

### t\_typesafety\_output\_of\_get\_default\_image ###

```javascript
      t_typesafety_output_of_get_default_image:any()

```

## on\_open

## on\_close

## on\_error

## start\_websocket

### t\_typesafety\_input\_of\_start\_websocket ###

```javascript
      t_typesafety_input_of_start_websocket:nargs()

```

### t\_typesafety\_output\_of\_start\_websocket ###

```javascript
      t_typesafety_output_of_start_websocket:any()

```

## stop\_websocket

### t\_typesafety\_input\_of\_stop\_websocket ###

```javascript
      t_typesafety_input_of_stop_websocket:nargs()

```

### t\_typesafety\_output\_of\_stop\_websocket ###

```javascript
      t_typesafety_output_of_stop_websocket:any()

```

## reveal\_identity\_via\_token

### t\_typesafety\_input\_of\_reveal\_identity\_via\_token ###

```javascript
      t_typesafety_input_of_reveal_identity_via_token:array(
        object(
          token : string()
        )
      )

```

### t\_typesafety\_output\_of\_reveal\_identity\_via\_token ###

```javascript
      t_typesafety_output_of_reveal_identity_via_token:equals( << true >>  )

```

## initialize\_identity

### t\_typesafety\_input\_of\_initialize\_identity ###

```javascript
      t_typesafety_input_of_initialize_identity:nargs()

```

### t\_typesafety\_output\_of\_initialize\_identity ###

```javascript
      t_typesafety_output_of_initialize_identity:equals( << true >>  )

```

## finalize\_identity

### t\_typesafety\_input\_of\_finalize\_identity ###

```javascript
      t_typesafety_input_of_finalize_identity:nargs()

```

### t\_typesafety\_output\_of\_finalize\_identity ###

```javascript
      t_typesafety_output_of_finalize_identity:equals( << true >>  )

```

## listen\_database\_channel

### t\_typesafety\_input\_of\_listen\_database\_channel ###

```javascript
      t_typesafety_input_of_listen_database_channel:nargs(
        channel_id : regexp(<< /^[0-9a-zA-Z_-]+$/ >> )
      )

```

### t\_typesafety\_output\_of\_listen\_database\_channel ###

```javascript
      t_typesafety_output_of_listen_database_channel:equals( << true >>  )

```

## unlisten\_database\_channel

### t\_typesafety\_input\_of\_unlisten\_database\_channel ###

```javascript
      t_typesafety_input_of_unlisten_database_channel:nargs(
        channel_id : uuid()
      )

```

### t\_typesafety\_output\_of\_unlisten\_database\_channel ###

```javascript
      t_typesafety_output_of_unlisten_database_channel:equals( << true >>  )

```

## unlisten\_all\_database\_channel

### t\_typesafety\_input\_of\_unlisten\_all\_database\_channel ###

```javascript
      t_typesafety_input_of_unlisten_all_database_channel:nargs()

```

### t\_typesafety\_output\_of\_unlisten\_all\_database\_channel ###

```javascript
      t_typesafety_output_of_unlisten_all_database_channel:equals( << true >>  )

```

Conclusion
=======================
