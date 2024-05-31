
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
t\_read\_accounts\_mode is a enumeration type which specifies
the mode when a user calls read\_accounts() method.

See read\_accounts()

```javascript
      /*          
      * t_read_accounts_mode is a enumeration type which specifies
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

get\_intl\_message
----------------

### \_\_t\_anonymous ###
test FOOOO

```javascript
      array(
        or(
          object(
            path    : array_of( string() ),
            lang_id : or( string(), null() ),
          ),
        )
      )
```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      array(
        or(
          object(
            lang_id : or( string(), null() ),
          ),
        )
      )
```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      array( string() )
```

### \_\_t\_anonymous ###

```javascript
      array_of( any() )
```

### \_\_t\_anonymous ###

```javascript
      nargs(
        user : object(
          username : string(),
        ),
      )

```

### \_\_t\_anonymous ###

```javascript
      object(
        user : object(
          username : string(),
        ),
      ),
```

### \_\_t\_anonymous ###

```javascript
      nargs(
        user : t_username_or_user_id(),
      )

```

### \_\_t\_anonymous ###

```javascript
      object(
        user : object(
          user_id  : t_user_id(),
          username : t_username(),
        ),
      ),
```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      object(
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

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs(
        username : t_username(),
      )

```

### \_\_t\_anonymous ###

```javascript
      object(
        user_id: t_user_id(),
      )

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      fold_right(
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

### \_\_t\_anonymous ###

```javascript
      array_of(
        object(
          wallet_id   : uuid(),
          valuable_id : uuid(),
          valuable_name : string(),
          current_valuable_quantity : string(),
        )
      )

```

### \_\_t\_anonymous ###

```javascript
      array(t_user_identity_token())
```

### \_\_t\_anonymous ###

```javascript
      t_user_login_info()
```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      boolean()
```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      array(
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

### \_\_t\_anonymous ###

```javascript
      object(
        user_id  : or( t_user_id(),  null()      ),
        username : or( t_username(), undefined() ),
      )

```

### \_\_t\_anonymous ###

```javascript
      array(
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

### \_\_t\_anonymous ###

```javascript
      object(
        member_user_id  : or( t_user_id(), null() ),
        member_username : or( t_username(), undefined() ),
      )

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs(
        username : or( t_username(), null() ),
        mode     : or( t_read_accounts_mode(), null() ),
      )

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs(
        timeline : or(
          object(),
          object(
            timeline_id : uuid(),
          ),
        ),
      )

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      fold_right(
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

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      array(
        object(
          valuable_id      : uuid(),
          valuable_enabled : boolean(),
        )
      )
```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      array(
        object(
          valuable_id      : uuid(),
        )
      )

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      array(
        object(
          message_text         : string(),
        )
      )
```

### \_\_t\_anonymous ###

```javascript
      object(
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

### \_\_t\_anonymous ###

```javascript
      fold_right(
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

### \_\_t\_anonymous ###

```javascript
      any(),
```

### \_\_t\_anonymous ###

```javascript
      nargs(
        scope_id : t_scope_id(),
        user_id  : t_user_id(),
      ),
```

### \_\_t\_anonymous ###

```javascript
      t_tbl_user_timelines(),
```

### \_\_t\_anonymous ###

```javascript
      nargs(
        scope_id : t_scope_id(),
        user_id  :t_user_id(),
        member_user_id : t_user_id(),
      ),
```

### \_\_t\_anonymous ###

```javascript
      t_tbl_user_member_timelines(),
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

### \_\_t\_anonymous ###

```javascript
      fold_right(
        object(
          valuable_id       : uuid(),
          valuable_quantity : number(),
          from_wallet_id    : uuid(),
          to_wallet_id      : uuid(),
          message_id        : or( uuid() , null() ),
        )
      )

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      fold_right(
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

### \_\_t\_anonymous ###

```javascript
      undefined(),
```

### \_\_t\_anonymous ###

```javascript
      fold_right(
        t_sndmsg_cmd_base()
      )

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      array(
        t_sndmsg_cmd(),
      )

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      fold_right(
        t_sndmsg_cmd(),
      )

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs(
        valuable_id : uuid(),
        from : or( string(), null() ),
        to   : or( string(), null() ),
      )

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs(
        valuable_id : uuid(),
      )

```

### \_\_t\_anonymous ###

```javascript
      any()

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

### \_\_t\_anonymous ###

```javascript
      nargs(
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

### \_\_t\_anonymous ###

```javascript
      any()
```

### \_\_t\_anonymous ###

```javascript
      nargs(
        user_id                : t_user_id(),
        scope_id               : t_scope_id(),
        default_parent_user_id : t_user_id(),
        parent_message_id      : or( uuid(), null() ),
        message_text           : string(),
        message_content_type   : or( null(), t_message_content_type() ),
      )

```

### \_\_t\_anonymous ###

```javascript
      any()
```

### \_\_t\_anonymous ###

```javascript
      array(
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

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      array_of(
        string()
      )

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      array()
```

### \_\_t\_anonymous ###

```javascript
      uuid()
```

### \_\_t\_anonymous ###

```javascript
      nargs(
        user_id : t_user_id(),
        timelinename : t_timelinename(),
        timeline_id : or(
          t_timeline_id(),
          null(),
          undefined(),
        )
      )

```

### \_\_t\_anonymous ###

```javascript
      object(
        timeline_id : t_timeline_id(),
      )

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      fold_right(
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

### \_\_t\_anonymous ###

```javascript
      t_tbl_user_member_timelines()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      fold_right(
        object(
          user_id                : t_user_id(),
          scope_id               : t_scope_id(),
          default_parent_user_id : t_user_id(),
          parent_message_id      : or( uuid(), null() ),
          message_content_type   : t_message_content_type(),
        )
      )

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      any()

```

### \_\_t\_anonymous ###

```javascript
      array(
        object(
          token : string()
        )
      )

```

### \_\_t\_anonymous ###

```javascript
      equals( << true >>  )

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      equals( << true >>  )

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      equals( << true >>  )

```

### \_\_t\_anonymous ###

```javascript
      nargs(
        channel_id : regexp(<< /^[0-9a-zA-Z_-]+$/ >> )
      )

```

### \_\_t\_anonymous ###

```javascript
      equals( << true >>  )

```

### \_\_t\_anonymous ###

```javascript
      nargs(
        channel_id : uuid()
      )

```

### \_\_t\_anonymous ###

```javascript
      equals( << true >>  )

```

### \_\_t\_anonymous ###

```javascript
      nargs()

```

### \_\_t\_anonymous ###

```javascript
      equals( << true >>  )

```

Conclusion
=======================
