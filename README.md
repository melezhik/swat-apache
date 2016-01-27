# SYNOPSIS

[swat](https://github.com/melezhik/swat) smoke/integration tests for apache server

# Check list

* verify that landing page request (`GET /`)  succeeds
* verify that apache footprint exists in server response
* verify that given string exists at landing page


# INSTALL

    cpanm Sparrow # you need Sparrow manager
    yum install curl
    sparrow index update
    sparrow plg install swat-apache # you need test suite swat-apache

# Running tests

    sparrow project create  apache
    sparrow check   add     apache apache-test
    sparrow check   set     apache apache-test swat-apache 127.0.0.1
    sparrow check   ini     apache apache-test 

        [apache]
        welcome_message   = 'It works'

    sparrow check run apache apache-test


# Sample output

    /home/vagrant/.swat/.cache/15332/prove/00.GET.t ..
    ok 1 - GET 127.0.0.1/ succeeded
    # response http headers saved to /home/vagrant/.swat/.cache/15332/prove/DaZ3xbDc8u.hdr
    # response body saved to /home/vagrant/.swat/.cache/15332/prove/DaZ3xbDc8u
    ok 2 - output match '200 OK'
    ok 3 - output match /Server: Apache/
    ok 4 - output match 'It works'
    1..4
    ok
    All tests successful.
    Files=1, Tests=4,  0 wallclock secs ( 0.06 usr  0.01 sys +  0.09 cusr  0.01 csys =  0.17 CPU)
    Result: PASS
    
# Author

[Alexey Melezhik](mailto:melezhik@gmail.com)


