# Instagram Ruby library

So far, the only way to browse [Instagram][] photos was their iPhone app. Well, no more.

This library acts as a client for the [unofficial Instagram API][wiki]. You can:

* fetch popular photos;
* get user info;
* browse photos by a user.

Caveat: you need to know user IDs; usernames can't be used. However, you can start from the popular feed and drill down from there.

## Example usage

    require 'instagram'
    
    photos = Instagram::popular
    photo = photos.first
    
    photo.caption     #=> "Extreme dog closeup"
    photo.likes.size  #=> 54
    
    photo.user.username      #=> "johndoe"
    photo.user.full_name     #=> "John Doe"
    photo.comments[1].text   #=> "That's so cute"
    photo.images.last.width  #=> 612
    
    
    # fetch extended info for John
    john_info = Instagram::user_info(photo.user.id)
    
    john_info.media_count   #=> 32
    john_info.followers     #=> 160
    
    
    # find more photos by John
    photos_by_john = Instagram::by_user(photo.user.id)


## Credits

Instagram API reverse-engineered and Ruby library written by Mislav Marohnić.


[instagram]: http://instagr.am/
[wiki]: https://github.com/mislav/instagram/wiki "Instagram API"