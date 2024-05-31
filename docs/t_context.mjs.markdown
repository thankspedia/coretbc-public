
  Documentation
=====================

get\_intl\_message
----------------

get\_intl\_message
-------------

get\_intl\_message

### t\_get\_intl\_message\_input ###
test FOOOO

```javascript
      /*          
      * test FOOOO
      */
      t_get_intl_message_input:array(
        or(
          object(
            path    : array_of( string() ),
            lang_id : or( string(), null() ),
          ),
        )
      )
```

### t\_get\_intl\_message\_output ###

```javascript
      t_get_intl_message_output:any()

```

get\_intl\_messages
-------------

get\_intl\_messages

### t\_get\_intl\_messages\_input ###

```javascript
      t_get_intl_messages_input:array(
        or(
          object(
            lang_id : or( string(), null() ),
          ),
        )
      )
```

### t\_get\_intl\_messages\_output ###

```javascript
      t_get_intl_messages_output:any()

```

get\_available\_intl\_messages
-------------

get\_available\_intl\_messages

### t\_get\_available\_intl\_messages\_input ###

```javascript
      t_get_available_intl_messages_input:array( string() )
```

### t\_get\_available\_intl\_messages\_output ###

```javascript
      t_get_available_intl_messages_output:array_of( any() )
```

create\_or\_update\_user
-------------

create\_or\_update\_user

### t\_create\_or\_update\_user\_input ###

```javascript
      t_create_or_update_user_input:nargs(
        user : object(
          username : string(),
        ),
      )

```

### t\_create\_or\_update\_user\_output ###

```javascript
      t_create_or_update_user_output:object(
        user : object(
          username : string(),
        ),
      ),
```

delete\_user
-------------

delete\_user

### t\_delete\_user\_input ###

```javascript
      t_delete_user_input:nargs(
        user : t_username_or_user_id(),
      )

```

### t\_delete\_user\_output ###

```javascript
      t_delete_user_output:object(
        user : object(
          user_id  : t_user_id(),
          username : t_username(),
        ),
      ),
```

delete\_multiple\_users
-------------

delete\_multiple\_users

### t\_delete\_multiple\_users\_input ###

```javascript
      t_delete_multiple_users_input:nargs()

```

### t\_delete\_multiple\_users\_output ###

```javascript
      t_delete_multiple_users_output:any()

```

has\_user
-------------

has\_user

### t\_has\_user\_input ###

```javascript
      t_has_user_input:nargs()

```

### t\_has\_user\_output ###

```javascript
      t_has_user_output:any()

```

has\_username
-------------

has\_username

### t\_has\_username\_input ###

```javascript
      t_has_username_input:nargs()

```

### t\_has\_username\_output ###

```javascript
      t_has_username_output:any()

```

read\_user
-------------

read\_user

### t\_read\_user\_input ###

```javascript
      t_read_user_input:nargs()

```

### t\_read\_user\_output ###

```javascript
      t_read_user_output:object(
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

user\_id2username
-------------

user\_id2username

### t\_user\_id2username\_input ###

```javascript
      t_user_id2username_input:nargs()

```

### t\_user\_id2username\_output ###

```javascript
      t_user_id2username_output:any()

```

username2user\_id
-------------

username2user\_id

### t\_username2user\_id\_input ###

```javascript
      t_username2user_id_input:nargs(
        username : t_username(),
      )

```

### t\_username2user\_id\_output ###

```javascript
      t_username2user_id_output:object(
        user_id: t_user_id(),
      )

```

read\_all\_users
-------------

read\_all\_users

### t\_read\_all\_users\_input ###

```javascript
      t_read_all_users_input:nargs()

```

### t\_read\_all\_users\_output ###

```javascript
      t_read_all_users_output:any()

```

count\_all\_users
-------------

count\_all\_users

### t\_count\_all\_users\_input ###

```javascript
      t_count_all_users_input:nargs()

```

### t\_count\_all\_users\_output ###

```javascript
      t_count_all_users_output:any()

```

create\_or\_update\_user\_authentication
-------------

create\_or\_update\_user\_authentication

### t\_create\_or\_update\_user\_authentication\_input ###

```javascript
      t_create_or_update_user_authentication_input:nargs()

```

### t\_create\_or\_update\_user\_authentication\_output ###

```javascript
      t_create_or_update_user_authentication_output:any()

```

update\_user\_authentication
-------------

update\_user\_authentication

### t\_update\_user\_authentication\_input ###

```javascript
      t_update_user_authentication_input:nargs()

```

### t\_update\_user\_authentication\_output ###

```javascript
      t_update_user_authentication_output:any()

```

read\_user\_authentication
-------------

read\_user\_authentication

### t\_read\_user\_authentication\_input ###

```javascript
      t_read_user_authentication_input:nargs()

```

### t\_read\_user\_authentication\_output ###

```javascript
      t_read_user_authentication_output:any()

```

delete\_user\_authentication
-------------

delete\_user\_authentication

### t\_delete\_user\_authentication\_input ###

```javascript
      t_delete_user_authentication_input:nargs()

```

### t\_delete\_user\_authentication\_output ###

```javascript
      t_delete_user_authentication_output:any()

```

read\_all\_user\_authentications
-------------

read\_all\_user\_authentications

### t\_read\_all\_user\_authentications\_input ###

```javascript
      t_read_all_user_authentications_input:nargs()

```

### t\_read\_all\_user\_authentications\_output ###

```javascript
      t_read_all_user_authentications_output:any()

```

get\_parent\_users
-------------

get\_parent\_users

### t\_get\_parent\_users\_input ###

```javascript
      t_get_parent_users_input:nargs()

```

### t\_get\_parent\_users\_output ###

```javascript
      t_get_parent_users_output:any()

```

get\_wallet\_contents
-------------

get\_wallet\_contents

### t\_get\_wallet\_contents\_input ###

```javascript
      t_get_wallet_contents_input:fold_right(
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

### t\_get\_wallet\_contents\_output ###

```javascript
      t_get_wallet_contents_output:array_of(
        object(
          wallet_id   : uuid(),
          valuable_id : uuid(),
          valuable_name : string(),
          current_valuable_quantity : string(),
        )
      )

```

abstract\_login
-------------

abstract\_login

### t\_abstract\_login\_input ###

```javascript

```

### t\_abstract\_login\_output ###

```javascript

```

abstract\_login\_information
-------------

abstract\_login\_information

### t\_abstract\_login\_information\_input ###

```javascript
      t_abstract_login_information_input:array(t_user_identity_token())
```

### t\_abstract\_login\_information\_output ###

```javascript
      t_abstract_login_information_output:t_user_login_info()
```

abstract\_switch\_current\_user
-------------

abstract\_switch\_current\_user

### t\_abstract\_switch\_current\_user\_input ###

```javascript
      t_abstract_switch_current_user_input:nargs()

```

### t\_abstract\_switch\_current\_user\_output ###

```javascript
      t_abstract_switch_current_user_output:boolean()
```

read\_user\_member
-------------

read\_user\_member

### t\_read\_user\_member\_input ###

```javascript
      t_read_user_member_input:nargs()

```

### t\_read\_user\_member\_output ###

```javascript
      t_read_user_member_output:any()

```

var\_ensure\_user\_id
-------------

var\_ensure\_user\_id

### t\_var\_ensure\_user\_id\_input ###

```javascript
      t_var_ensure_user_id_input:array(
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

### t\_var\_ensure\_user\_id\_output ###

```javascript
      t_var_ensure_user_id_output:object(
        user_id  : or( t_user_id(),  null()      ),
        username : or( t_username(), undefined() ),
      )

```

var\_ensure\_member\_user\_id
-------------

var\_ensure\_member\_user\_id

### t\_var\_ensure\_member\_user\_id\_input ###

```javascript
      t_var_ensure_member_user_id_input:array(
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

### t\_var\_ensure\_member\_user\_id\_output ###

```javascript
      t_var_ensure_member_user_id_output:object(
        member_user_id  : or( t_user_id(), null() ),
        member_username : or( t_username(), undefined() ),
      )

```

create\_or\_update\_user\_member
-------------

create\_or\_update\_user\_member

### t\_create\_or\_update\_user\_member\_input ###

```javascript
      t_create_or_update_user_member_input:nargs()

```

### t\_create\_or\_update\_user\_member\_output ###

```javascript
      t_create_or_update_user_member_output:any()

```

delete\_user\_member
-------------

delete\_user\_member

### t\_delete\_user\_member\_input ###

```javascript
      t_delete_user_member_input:nargs()

```

### t\_delete\_user\_member\_output ###

```javascript
      t_delete_user_member_output:any()

```

delete\_multiple\_user\_members
-------------

delete\_multiple\_user\_members

### t\_delete\_multiple\_user\_members\_input ###

```javascript
      t_delete_multiple_user_members_input:nargs()

```

### t\_delete\_multiple\_user\_members\_output ###

```javascript
      t_delete_multiple_user_members_output:any()

```

read\_filtered\_user\_members
-------------

read\_filtered\_user\_members

### t\_read\_filtered\_user\_members\_input ###

```javascript
      t_read_filtered_user_members_input:nargs()

```

### t\_read\_filtered\_user\_members\_output ###

```javascript
      t_read_filtered_user_members_output:any()

```

read\_accounts
-------------

read\_accounts

### t\_read\_accounts\_input ###

```javascript
      t_read_accounts_input:nargs(
        username : or( t_username(), null() ),
        mode     : or( t_read_accounts_mode(), null() ),
      )

```

### t\_read\_accounts\_output ###

```javascript
      t_read_accounts_output:any()

```

create\_or\_update\_account
-------------

create\_or\_update\_account

### t\_create\_or\_update\_account\_input ###

```javascript
      t_create_or_update_account_input:nargs()

```

### t\_create\_or\_update\_account\_output ###

```javascript
      t_create_or_update_account_output:any()

```

create\_or\_update\_accounts
-------------

create\_or\_update\_accounts

### t\_create\_or\_update\_accounts\_input ###

```javascript
      t_create_or_update_accounts_input:nargs()

```

### t\_create\_or\_update\_accounts\_output ###

```javascript
      t_create_or_update_accounts_output:any()

```

create\_message
-------------

create\_message

### t\_create\_message\_input ###

```javascript
      t_create_message_input:nargs()

```

### t\_create\_message\_output ###

```javascript
      t_create_message_output:any()

```

write\_message
-------------

write\_message

### t\_write\_message\_input ###

```javascript
      t_write_message_input:nargs()

```

### t\_write\_message\_output ###

```javascript
      t_write_message_output:any()

```

read\_message
-------------

read\_message

### t\_read\_message\_input ###

```javascript
      t_read_message_input:nargs()

```

### t\_read\_message\_output ###

```javascript
      t_read_message_output:any()

```

delete\_message
-------------

delete\_message

### t\_delete\_message\_input ###

```javascript
      t_delete_message_input:nargs()

```

### t\_delete\_message\_output ###

```javascript
      t_delete_message_output:any()

```

test\_stored\_procedure
-------------

test\_stored\_procedure

### t\_test\_stored\_procedure\_input ###

```javascript
      t_test_stored_procedure_input:nargs()

```

### t\_test\_stored\_procedure\_output ###

```javascript
      t_test_stored_procedure_output:any()

```

create\_timeline
-------------

create\_timeline

### t\_create\_timeline\_input ###

```javascript
      t_create_timeline_input:nargs(
        timeline : or(
          object(),
          object(
            timeline_id : uuid(),
          ),
        ),
      )

```

### t\_create\_timeline\_output ###

```javascript
      t_create_timeline_output:any()

```

read\_timeline
-------------

read\_timeline

### t\_read\_timeline\_input ###

```javascript
      t_read_timeline_input:nargs()

```

### t\_read\_timeline\_output ###

```javascript
      t_read_timeline_output:any()

```

delete\_timeline
-------------

delete\_timeline

### t\_delete\_timeline\_input ###

```javascript
      t_delete_timeline_input:nargs()

```

### t\_delete\_timeline\_output ###

```javascript
      t_delete_timeline_output:any()

```

read\_view\_timeline\_and\_profile
-------------

read\_view\_timeline\_and\_profile

### t\_read\_view\_timeline\_and\_profile\_input ###

```javascript
      t_read_view_timeline_and_profile_input:nargs()

```

### t\_read\_view\_timeline\_and\_profile\_output ###

```javascript
      t_read_view_timeline_and_profile_output:any()

```

create\_or\_update\_view\_user\_and\_user\_timeline\_and\_timeline\_and\_profile
-------------

create\_or\_update\_view\_user\_and\_user\_timeline\_and\_timeline\_and\_profile

### t\_create\_or\_update\_view\_user\_and\_user\_timeline\_and\_timeline\_and\_profile\_input ###

```javascript
      t_create_or_update_view_user_and_user_timeline_and_timeline_and_profile_input:fold_right(
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

### t\_create\_or\_update\_view\_user\_and\_user\_timeline\_and\_timeline\_and\_profile\_output ###

```javascript
      t_create_or_update_view_user_and_user_timeline_and_timeline_and_profile_output:any()

```

create\_or\_update\_view\_user\_member\_and\_user\_timeline\_and\_timeline\_and\_profile
-------------

create\_or\_update\_view\_user\_member\_and\_user\_timeline\_and\_timeline\_and\_profile

### t\_create\_or\_update\_view\_user\_member\_and\_user\_timeline\_and\_timeline\_and\_profile\_input ###

```javascript
      t_create_or_update_view_user_member_and_user_timeline_and_timeline_and_profile_input:nargs()

```

### t\_create\_or\_update\_view\_user\_member\_and\_user\_timeline\_and\_timeline\_and\_profile\_output ###

```javascript
      t_create_or_update_view_user_member_and_user_timeline_and_timeline_and_profile_output:any()

```

read\_view\_users\_and\_user\_timeline\_and\_timeline\_and\_profile
-------------

read\_view\_users\_and\_user\_timeline\_and\_timeline\_and\_profile

### t\_read\_view\_users\_and\_user\_timeline\_and\_timeline\_and\_profile\_input ###

```javascript
      t_read_view_users_and_user_timeline_and_timeline_and_profile_input:nargs()

```

### t\_read\_view\_users\_and\_user\_timeline\_and\_timeline\_and\_profile\_output ###

```javascript
      t_read_view_users_and_user_timeline_and_timeline_and_profile_output:any()

```

read\_view\_user\_member\_and\_user\_timeline\_and\_timeline\_and\_profile
-------------

read\_view\_user\_member\_and\_user\_timeline\_and\_timeline\_and\_profile

### t\_read\_view\_user\_member\_and\_user\_timeline\_and\_timeline\_and\_profile\_input ###

```javascript
      t_read_view_user_member_and_user_timeline_and_timeline_and_profile_input:nargs()

```

### t\_read\_view\_user\_member\_and\_user\_timeline\_and\_timeline\_and\_profile\_output ###

```javascript
      t_read_view_user_member_and_user_timeline_and_timeline_and_profile_output:any()

```

user\_timelines\_to\_object
-------------

user\_timelines\_to\_object

### t\_user\_timelines\_to\_object\_input ###

```javascript
      t_user_timelines_to_object_input:nargs()

```

### t\_user\_timelines\_to\_object\_output ###

```javascript
      t_user_timelines_to_object_output:any()

```

object\_to\_user\_timelines
-------------

object\_to\_user\_timelines

### t\_object\_to\_user\_timelines\_input ###

```javascript
      t_object_to_user_timelines_input:nargs()

```

### t\_object\_to\_user\_timelines\_output ###

```javascript
      t_object_to_user_timelines_output:any()

```

create\_or\_update\_profile
-------------

create\_or\_update\_profile

### t\_create\_or\_update\_profile\_input ###

```javascript
      t_create_or_update_profile_input:nargs()

```

### t\_create\_or\_update\_profile\_output ###

```javascript
      t_create_or_update_profile_output:any()

```

read\_profile
-------------

read\_profile

### t\_read\_profile\_input ###

```javascript
      t_read_profile_input:nargs()

```

### t\_read\_profile\_output ###

```javascript
      t_read_profile_output:any()

```

delete\_profile
-------------

delete\_profile

### t\_delete\_profile\_input ###

```javascript
      t_delete_profile_input:nargs()

```

### t\_delete\_profile\_output ###

```javascript
      t_delete_profile_output:any()

```

create\_timeline\_content
-------------

create\_timeline\_content

### t\_create\_timeline\_content\_input ###

```javascript
      t_create_timeline_content_input:nargs()

```

### t\_create\_timeline\_content\_output ###

```javascript
      t_create_timeline_content_output:any()

```

read\_timeline\_content
-------------

read\_timeline\_content

### t\_read\_timeline\_content\_input ###

```javascript
      t_read_timeline_content_input:nargs()

```

### t\_read\_timeline\_content\_output ###

```javascript
      t_read_timeline_content_output:any()

```

delete\_timeline\_content
-------------

delete\_timeline\_content

### t\_delete\_timeline\_content\_input ###

```javascript
      t_delete_timeline_content_input:nargs()

```

### t\_delete\_timeline\_content\_output ###

```javascript
      t_delete_timeline_content_output:any()

```

is\_timeline\_following
-------------

is\_timeline\_following

### t\_is\_timeline\_following\_input ###

```javascript
      t_is_timeline_following_input:nargs()

```

### t\_is\_timeline\_following\_output ###

```javascript
      t_is_timeline_following_output:any()

```

follow\_timeline
-------------

follow\_timeline

### t\_follow\_timeline\_input ###

```javascript
      t_follow_timeline_input:nargs()

```

### t\_follow\_timeline\_output ###

```javascript
      t_follow_timeline_output:any()

```

unfollow\_timeline
-------------

unfollow\_timeline

### t\_unfollow\_timeline\_input ###

```javascript
      t_unfollow_timeline_input:nargs()

```

### t\_unfollow\_timeline\_output ###

```javascript
      t_unfollow_timeline_output:any()

```

create\_or\_update\_valuable
-------------

create\_or\_update\_valuable

### t\_create\_or\_update\_valuable\_input ###

```javascript
      t_create_or_update_valuable_input:nargs()

```

### t\_create\_or\_update\_valuable\_output ###

```javascript
      t_create_or_update_valuable_output:any()

```

create\_valuable
-------------

create\_valuable

### t\_create\_valuable\_input ###

```javascript
      t_create_valuable_input:nargs()

```

### t\_create\_valuable\_output ###

```javascript
      t_create_valuable_output:any()

```

update\_valuable
-------------

update\_valuable

### t\_update\_valuable\_input ###

```javascript
      t_update_valuable_input:nargs()

```

### t\_update\_valuable\_output ###

```javascript
      t_update_valuable_output:any()

```

disableValuable
-------------

disableValuable

### t\_disableValuable\_input ###

```javascript
      t_disableValuable_input:nargs()

```

### t\_disableValuable\_output ###

```javascript
      t_disableValuable_output:any()

```

read\_valuable
-------------

read\_valuable

### t\_read\_valuable\_input ###

```javascript
      t_read_valuable_input:nargs()

```

### t\_read\_valuable\_output ###

```javascript
      t_read_valuable_output:any()

```

delete\_valuable
-------------

delete\_valuable

### t\_delete\_valuable\_input ###

```javascript
      t_delete_valuable_input:nargs()

```

### t\_delete\_valuable\_output ###

```javascript
      t_delete_valuable_output:any()

```

read\_all\_valuables
-------------

read\_all\_valuables

### t\_read\_all\_valuables\_input ###

```javascript
      t_read_all_valuables_input:nargs()

```

### t\_read\_all\_valuables\_output ###

```javascript
      t_read_all_valuables_output:any()

```

issue\_valuables
-------------

issue\_valuables

### t\_issue\_valuables\_input ###

```javascript
      t_issue_valuables_input:nargs()

```

### t\_issue\_valuables\_output ###

```javascript
      t_issue_valuables_output:any()

```

update\_valuable\_state
-------------

update\_valuable\_state

### t\_update\_valuable\_state\_input ###

```javascript
      t_update_valuable_state_input:array(
        object(
          valuable_id      : uuid(),
          valuable_enabled : boolean(),
        )
      )
```

### t\_update\_valuable\_state\_output ###

```javascript
      t_update_valuable_state_output:any()

```

download\_valuable\_state
-------------

download\_valuable\_state

### t\_download\_valuable\_state\_input ###

```javascript
      t_download_valuable_state_input:array(
        object(
          valuable_id      : uuid(),
        )
      )

```

### t\_download\_valuable\_state\_output ###

```javascript
      t_download_valuable_state_output:any()

```

confiscate\_all\_valuable\_deposits
-------------

confiscate\_all\_valuable\_deposits

### t\_confiscate\_all\_valuable\_deposits\_input ###

```javascript
      t_confiscate_all_valuable_deposits_input:nargs()

```

### t\_confiscate\_all\_valuable\_deposits\_output ###

```javascript
      t_confiscate_all_valuable_deposits_output:any()

```

create\_wallet
-------------

create\_wallet

### t\_create\_wallet\_input ###

```javascript
      t_create_wallet_input:nargs()

```

### t\_create\_wallet\_output ###

```javascript
      t_create_wallet_output:any()

```

update\_wallet
-------------

update\_wallet

### t\_update\_wallet\_input ###

```javascript
      t_update_wallet_input:nargs()

```

### t\_update\_wallet\_output ###

```javascript
      t_update_wallet_output:any()

```

disableWallet
-------------

disableWallet

### t\_disableWallet\_input ###

```javascript
      t_disableWallet_input:nargs()

```

### t\_disableWallet\_output ###

```javascript
      t_disableWallet_output:any()

```

read\_wallet
-------------

read\_wallet

### t\_read\_wallet\_input ###

```javascript
      t_read_wallet_input:nargs()

```

### t\_read\_wallet\_output ###

```javascript
      t_read_wallet_output:any()

```

delete\_wallet
-------------

delete\_wallet

### t\_delete\_wallet\_input ###

```javascript
      t_delete_wallet_input:nargs()

```

### t\_delete\_wallet\_output ###

```javascript
      t_delete_wallet_output:any()

```

request\_valuable\_transfer
-------------

request\_valuable\_transfer

### t\_request\_valuable\_transfer\_input ###

```javascript
      t_request_valuable_transfer_input:nargs()

```

### t\_request\_valuable\_transfer\_output ###

```javascript
      t_request_valuable_transfer_output:any()

```

respond\_valuable\_transfer
-------------

respond\_valuable\_transfer

### t\_respond\_valuable\_transfer\_input ###

```javascript
      t_respond_valuable_transfer_input:nargs()

```

### t\_respond\_valuable\_transfer\_output ###

```javascript
      t_respond_valuable_transfer_output:any()

```

parse\_message\_commands
-------------

parse\_message\_commands

### t\_parse\_message\_commands\_input ###

```javascript
      t_parse_message_commands_input:array(
        object(
          message_text         : string(),
        )
      )
```

### t\_parse\_message\_commands\_output ###

```javascript
      t_parse_message_commands_output:object(
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

execute\_message\_commands
-------------

execute\_message\_commands

### t\_execute\_message\_commands\_input ###

```javascript
      t_execute_message_commands_input:fold_right(
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

### t\_execute\_message\_commands\_output ###

```javascript
      t_execute_message_commands_output:any(),
```

get\_notify\_timeline\_from\_user
-------------

get\_notify\_timeline\_from\_user

### t\_get\_notify\_timeline\_from\_user\_input ###

```javascript
      t_get_notify_timeline_from_user_input:nargs(
        scope_id : t_scope_id(),
        user_id  : t_user_id(),
      ),
```

### t\_get\_notify\_timeline\_from\_user\_output ###

```javascript
      t_get_notify_timeline_from_user_output:t_tbl_user_timelines(),
```

get\_notify\_timeline\_from\_member\_user
-------------

get\_notify\_timeline\_from\_member\_user

### t\_get\_notify\_timeline\_from\_member\_user\_input ###

```javascript
      t_get_notify_timeline_from_member_user_input:nargs(
        scope_id : t_scope_id(),
        user_id  :t_user_id(),
        member_user_id : t_user_id(),
      ),
```

### t\_get\_notify\_timeline\_from\_member\_user\_output ###

```javascript
      t_get_notify_timeline_from_member_user_output:t_tbl_user_member_timelines(),
```

sndmsg\_util\_transfer
-------------

sndmsg\_util\_transfer

### t\_sndmsg\_util\_transfer\_input ###

```javascript
      t_sndmsg_util_transfer_input:fold_right(
        object(
          valuable_id       : uuid(),
          valuable_quantity : number(),
          from_wallet_id    : uuid(),
          to_wallet_id      : uuid(),
          message_id        : or( uuid() , null() ),
        )
      )

```

### t\_sndmsg\_util\_transfer\_output ###

```javascript
      t_sndmsg_util_transfer_output:any()

```

sndmsg\_util\_notification
-------------

sndmsg\_util\_notification

### t\_sndmsg\_util\_notification\_input ###

```javascript
      t_sndmsg_util_notification_input:fold_right(
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

### t\_sndmsg\_util\_notification\_output ###

```javascript
      t_sndmsg_util_notification_output:undefined(),
```

sndmsg\_cmd\_message
-------------

sndmsg\_cmd\_message

### t\_sndmsg\_cmd\_message\_input ###

```javascript
      t_sndmsg_cmd_message_input:fold_right(
        t_sndmsg_cmd_base()
      )

```

### t\_sndmsg\_cmd\_message\_output ###

```javascript
      t_sndmsg_cmd_message_output:any()

```

sndmsg\_cmd\_check
-------------

sndmsg\_cmd\_check

### t\_sndmsg\_cmd\_check\_input ###

```javascript
      t_sndmsg_cmd_check_input:array(
        t_sndmsg_cmd(),
      )

```

### t\_sndmsg\_cmd\_check\_output ###

```javascript
      t_sndmsg_cmd_check_output:any()

```

sndmsg\_cmd\_valuable
-------------

sndmsg\_cmd\_valuable

### t\_sndmsg\_cmd\_valuable\_input ###

```javascript
      t_sndmsg_cmd_valuable_input:fold_right(
        t_sndmsg_cmd(),
      )

```

### t\_sndmsg\_cmd\_valuable\_output ###

```javascript
      t_sndmsg_cmd_valuable_output:any()

```

read\_valuable\_transactions
-------------

read\_valuable\_transactions

### t\_read\_valuable\_transactions\_input ###

```javascript
      t_read_valuable_transactions_input:nargs(
        valuable_id : uuid(),
        from : or( string(), null() ),
        to   : or( string(), null() ),
      )

```

### t\_read\_valuable\_transactions\_output ###

```javascript
      t_read_valuable_transactions_output:any()

```

read\_valuable\_deposits
-------------

read\_valuable\_deposits

### t\_read\_valuable\_deposits\_input ###

```javascript
      t_read_valuable_deposits_input:nargs(
        valuable_id : uuid(),
      )

```

### t\_read\_valuable\_deposits\_output ###

```javascript
      t_read_valuable_deposits_output:any()

```

send\_message
-------------

send\_message

### t\_send\_message\_input ###

```javascript
      t_send_message_input:nargs(
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

### t\_send\_message\_output ###

```javascript
      t_send_message_output:any()
```

send\_tweet
-------------

send\_tweet

### t\_send\_tweet\_input ###

```javascript
      t_send_tweet_input:nargs(
        user_id                : t_user_id(),
        scope_id               : t_scope_id(),
        default_parent_user_id : t_user_id(),
        parent_message_id      : or( uuid(), null() ),
        message_text           : string(),
        message_content_type   : or( null(), t_message_content_type() ),
      )

```

### t\_send\_tweet\_output ###

```javascript
      t_send_tweet_output:any()
```

receive\_tweets
-------------

receive\_tweets

### t\_receive\_tweets\_input ###

```javascript
      t_receive_tweets_input:array(
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

### t\_receive\_tweets\_output ###

```javascript
      t_receive_tweets_output:any()

```

get\_locale\_message
-------------

get\_locale\_message

### t\_get\_locale\_message\_input ###

```javascript
      t_get_locale_message_input:array_of(
        string()
      )

```

### t\_get\_locale\_message\_output ###

```javascript
      t_get_locale_message_output:any()

```

get\_global\_common\_input\_timeline\_id
-------------

get\_global\_common\_input\_timeline\_id

### t\_get\_global\_common\_input\_timeline\_id\_input ###

```javascript
      t_get_global_common_input_timeline_id_input:array()
```

### t\_get\_global\_common\_input\_timeline\_id\_output ###

```javascript
      t_get_global_common_input_timeline_id_output:uuid()
```

create\_or\_update\_user\_timeline
-------------

create\_or\_update\_user\_timeline

### t\_create\_or\_update\_user\_timeline\_input ###

```javascript
      t_create_or_update_user_timeline_input:nargs(
        user_id : t_user_id(),
        timelinename : t_timelinename(),
        timeline_id : or(
          t_timeline_id(),
          null(),
          undefined(),
        )
      )

```

### t\_create\_or\_update\_user\_timeline\_output ###

```javascript
      t_create_or_update_user_timeline_output:object(
        timeline_id : t_timeline_id(),
      )

```

read\_user\_timeline
-------------

read\_user\_timeline

### t\_read\_user\_timeline\_input ###

```javascript
      t_read_user_timeline_input:nargs()

```

### t\_read\_user\_timeline\_output ###

```javascript
      t_read_user_timeline_output:any()

```

delete\_user\_timeline
-------------

delete\_user\_timeline

### t\_delete\_user\_timeline\_input ###

```javascript
      t_delete_user_timeline_input:nargs()

```

### t\_delete\_user\_timeline\_output ###

```javascript
      t_delete_user_timeline_output:any()

```

create\_or\_update\_user\_watching\_timeline
-------------

create\_or\_update\_user\_watching\_timeline

### t\_create\_or\_update\_user\_watching\_timeline\_input ###

```javascript
      t_create_or_update_user_watching_timeline_input:nargs()

```

### t\_create\_or\_update\_user\_watching\_timeline\_output ###

```javascript
      t_create_or_update_user_watching_timeline_output:any()

```

read\_user\_watching\_timeline
-------------

read\_user\_watching\_timeline

### t\_read\_user\_watching\_timeline\_input ###

```javascript
      t_read_user_watching_timeline_input:nargs()

```

### t\_read\_user\_watching\_timeline\_output ###

```javascript
      t_read_user_watching_timeline_output:any()

```

delete\_user\_watching\_timeline
-------------

delete\_user\_watching\_timeline

### t\_delete\_user\_watching\_timeline\_input ###

```javascript
      t_delete_user_watching_timeline_input:nargs()

```

### t\_delete\_user\_watching\_timeline\_output ###

```javascript
      t_delete_user_watching_timeline_output:any()

```

create\_or\_update\_user\_member\_timeline
-------------

create\_or\_update\_user\_member\_timeline

### t\_create\_or\_update\_user\_member\_timeline\_input ###

```javascript
      t_create_or_update_user_member_timeline_input:nargs()

```

### t\_create\_or\_update\_user\_member\_timeline\_output ###

```javascript
      t_create_or_update_user_member_timeline_output:any()

```

read\_user\_member\_timeline
-------------

read\_user\_member\_timeline

### t\_read\_user\_member\_timeline\_input ###

```javascript
      t_read_user_member_timeline_input:fold_right(
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

### t\_read\_user\_member\_timeline\_output ###

```javascript
      t_read_user_member_timeline_output:t_tbl_user_member_timelines()

```

delete\_user\_member\_timeline
-------------

delete\_user\_member\_timeline

### t\_delete\_user\_member\_timeline\_input ###

```javascript
      t_delete_user_member_timeline_input:nargs()

```

### t\_delete\_user\_member\_timeline\_output ###

```javascript
      t_delete_user_member_timeline_output:any()

```

create\_or\_update\_user\_member\_watching\_timeline
-------------

create\_or\_update\_user\_member\_watching\_timeline

### t\_create\_or\_update\_user\_member\_watching\_timeline\_input ###

```javascript
      t_create_or_update_user_member_watching_timeline_input:nargs()

```

### t\_create\_or\_update\_user\_member\_watching\_timeline\_output ###

```javascript
      t_create_or_update_user_member_watching_timeline_output:any()

```

read\_user\_member\_watching\_timeline
-------------

read\_user\_member\_watching\_timeline

### t\_read\_user\_member\_watching\_timeline\_input ###

```javascript
      t_read_user_member_watching_timeline_input:nargs()

```

### t\_read\_user\_member\_watching\_timeline\_output ###

```javascript
      t_read_user_member_watching_timeline_output:any()

```

delete\_user\_member\_watching\_timeline
-------------

delete\_user\_member\_watching\_timeline

### t\_delete\_user\_member\_watching\_timeline\_input ###

```javascript
      t_delete_user_member_watching_timeline_input:nargs()

```

### t\_delete\_user\_member\_watching\_timeline\_output ###

```javascript
      t_delete_user_member_watching_timeline_output:any()

```

list\_child\_users
-------------

list\_child\_users

### t\_list\_child\_users\_input ###

```javascript
      t_list_child_users_input:nargs()

```

### t\_list\_child\_users\_output ###

```javascript
      t_list_child_users_output:any()

```

get\_random\_user
-------------

get\_random\_user

### t\_get\_random\_user\_input ###

```javascript
      t_get_random_user_input:nargs()

```

### t\_get\_random\_user\_output ###

```javascript
      t_get_random_user_output:any()

```

get\_random\_member\_user
-------------

get\_random\_member\_user

### t\_get\_random\_member\_user\_input ###

```javascript
      t_get_random_member_user_input:nargs()

```

### t\_get\_random\_member\_user\_output ###

```javascript
      t_get_random_member_user_output:any()

```

parse\_message\_text
-------------

parse\_message\_text

### t\_parse\_message\_text\_input ###

```javascript
      t_parse_message_text_input:nargs()

```

### t\_parse\_message\_text\_output ###

```javascript
      t_parse_message_text_output:any()

```

send\_random\_member\_user\_tweet
-------------

send\_random\_member\_user\_tweet

### t\_send\_random\_member\_user\_tweet\_input ###

```javascript
      t_send_random_member_user_tweet_input:nargs()

```

### t\_send\_random\_member\_user\_tweet\_output ###

```javascript
      t_send_random_member_user_tweet_output:any()

```

send\_random\_user\_tweet
-------------

send\_random\_user\_tweet

### t\_send\_random\_user\_tweet\_input ###

```javascript
      t_send_random_user_tweet_input:fold_right(
        object(
          user_id                : t_user_id(),
          scope_id               : t_scope_id(),
          default_parent_user_id : t_user_id(),
          parent_message_id      : or( uuid(), null() ),
          message_content_type   : t_message_content_type(),
        )
      )

```

### t\_send\_random\_user\_tweet\_output ###

```javascript
      t_send_random_user_tweet_output:any()

```

test\_blob
-------------

test\_blob

### t\_test\_blob\_input ###

```javascript
      t_test_blob_input:nargs()

```

### t\_test\_blob\_output ###

```javascript
      t_test_blob_output:any()

```

get\_default\_image
-------------

get\_default\_image

### t\_get\_default\_image\_input ###

```javascript
      t_get_default_image_input:nargs()

```

### t\_get\_default\_image\_output ###

```javascript
      t_get_default_image_output:any()

```

on\_open
-------------

on\_open

### t\_on\_open\_input ###

```javascript

```

### t\_on\_open\_output ###

```javascript

```

on\_close
-------------

on\_close

### t\_on\_close\_input ###

```javascript

```

### t\_on\_close\_output ###

```javascript

```

on\_error
-------------

on\_error

### t\_on\_error\_input ###

```javascript

```

### t\_on\_error\_output ###

```javascript

```

start\_websocket
-------------

start\_websocket

### t\_start\_websocket\_input ###

```javascript
      t_start_websocket_input:nargs()

```

### t\_start\_websocket\_output ###

```javascript
      t_start_websocket_output:any()

```

stop\_websocket
-------------

stop\_websocket

### t\_stop\_websocket\_input ###

```javascript
      t_stop_websocket_input:nargs()

```

### t\_stop\_websocket\_output ###

```javascript
      t_stop_websocket_output:any()

```

reveal\_identity\_via\_token
-------------

reveal\_identity\_via\_token

### t\_reveal\_identity\_via\_token\_input ###

```javascript
      t_reveal_identity_via_token_input:array(
        object(
          token : string()
        )
      )

```

### t\_reveal\_identity\_via\_token\_output ###

```javascript
      t_reveal_identity_via_token_output:equals( << true >>  )

```

initialize\_identity
-------------

initialize\_identity

### t\_initialize\_identity\_input ###

```javascript
      t_initialize_identity_input:nargs()

```

### t\_initialize\_identity\_output ###

```javascript
      t_initialize_identity_output:equals( << true >>  )

```

finalize\_identity
-------------

finalize\_identity

### t\_finalize\_identity\_input ###

```javascript
      t_finalize_identity_input:nargs()

```

### t\_finalize\_identity\_output ###

```javascript
      t_finalize_identity_output:equals( << true >>  )

```

listen\_database\_channel
-------------

listen\_database\_channel

### t\_listen\_database\_channel\_input ###

```javascript
      t_listen_database_channel_input:nargs(
        channel_id : regexp(<< /^[0-9a-zA-Z_-]+$/ >> )
      )

```

### t\_listen\_database\_channel\_output ###

```javascript
      t_listen_database_channel_output:equals( << true >>  )

```

unlisten\_database\_channel
-------------

unlisten\_database\_channel

### t\_unlisten\_database\_channel\_input ###

```javascript
      t_unlisten_database_channel_input:nargs(
        channel_id : uuid()
      )

```

### t\_unlisten\_database\_channel\_output ###

```javascript
      t_unlisten_database_channel_output:equals( << true >>  )

```

unlisten\_all\_database\_channel
-------------

unlisten\_all\_database\_channel

### t\_unlisten\_all\_database\_channel\_input ###

```javascript
      t_unlisten_all_database_channel_input:nargs()

```

### t\_unlisten\_all\_database\_channel\_output ###

```javascript
      t_unlisten_all_database_channel_output:equals( << true >>  )

```

Conclusion
=======================
