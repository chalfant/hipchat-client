hipchat-client
==============

A HipChat Client

[![NPM](https://nodei.co/npm/hipchat-client.png?downloads=true&stars=true)](https://nodei.co/npm/hipchat-client/)

### Installation

    $ npm install hipchat-client

### Usage

    var HipchatClient = require('hipchat-client');

##### Constructor

    var HipChat = new HipchatClient(auth_token);

##### Get user email by mention name

    HipChat.getMailByMentionName('mention_name', function (email) {
      console.log(email);
    });

##### Get room id by room name

    HipChat.getRoomByName('room_name', function (id) {
      console.log(id);
    });

##### Get room id by room Jid

    HipChat.getRoomByIdByJid('123_room@conf.hipchat.com', function (id)) {
      console.log(id);
    });

##### Get list of room participant Ids

    HipChat.getRoomParticipantIds(room_api_id, function (ids) {
      for (var i=0; i < ids.length; i++) {
        console.log( ids[i] );
      }
    });

##### Get list of all users in your account

    HipChat.getUsers( function (users) {
      for (var i=0; i < users.length; i++) {
        console.log( users[i].name );
      }
    });

##### Send message to a room

    var message = "<a href='http://hipchat.com'>HipChat</a>";
    var params = {
      from: 'HipChat',
      color: 'yellow',
      notify: 1
    };

    HipChat.sendRoomMessage(message, room_id, params, function (success) {
      console.log(success);
    });

##### Example: Send Message to a Room without room_id

    HipChat.getRoomByName('room_name', function (id) {
      var message = "<a href='http://hipchat.com'>HipChat</a>";
      var params = {
        from: 'HipChat',
        color: 'yellow',
        notify: 1
      };

      HipChat.sendRoomMessage(message, id, params, function (success) {
        console.log(success);
      });
    });


## Changelog

### v0.0.9

- Add message format to sendRoomMessage method (default to 'html').

### v0.0.8

- Fix a bug comparing in sendMessageRoom method.

## MIT License

Copyright (c) 2013 <germanrcuriel@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
