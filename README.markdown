
# raspell

An interface binding for the Aspell spelling checker.

## License

Copyright 2007, 2008 Cloudburst, LLC. Licensed under the GPL 2.0. See included LICENSE file. Portions copyright 2005 Matthias Veit, Biro Eszter and used with permission.  

The public certificate for the gem is [here][:pubcert]. 

If you use this software, please [make a donation][:donate], or [recommend Evan][:recommend] at Working with Rails.

## Requirements

Raspell requires Aspell version 0.6 ([http://www.aspell.net][:aspell]) and at least one Aspell dictionary. 

### Mac: 
    sudo port install aspell aspell-dict-en

### Ubuntu: 
    sudo apt-get install aspell libaspell-dev aspell-en
  
## Installation

### Mac:
    sudo gem install raspell -- --with-opt-dir=/opt/local
  
### Ubuntu:
    sudo gem install raspell
  
## Usage

Aspell lets you `check` words and `suggest` corrections. For example:
   
    require 'rubygems'
    require 'raspell'

    speller = Aspell.new("en_US")
    speller.suggestion_mode = Aspell::NORMAL

    string = "my haert wil go on"

    string.gsub(/[\w\']+/) do |word| 
      if !speller.check(word) 
        # word is wrong
        puts "Possible correction for #{word}:"
        puts speller.suggest(word).first
      end
    end

This outputs:

    Possible correction for haert:
    heart
    Possible correction for wil:
    Will

Note that `suggest` returns an array of suggestions even for words that are correctly spelled.

## Options

The most useful options are `suggestion_mode`, and the passthrough option `ignore_case`. Passthrough options have to be set as so:

    speller.set_option("ignore-case", "true")

See [http://aspell.net/man-html/The-Options.html][:aspell_options] for a list of the passthrough options. 

## Reporting problems

The support forum is [here][:forum].

Patches and contributions are very welcome. Please note that contributors are required to assign copyright for their additions to Cloudburst, LLC.

## Futher resources

* [add gud spelning to ur railz app or wharever][:additional_resource1]

[:pubcert]: http://rubyforge.org/frs/download.php/25331/evan_weaver-original-public_cert.pem
[:donate]: http://blog.evanweaver.com/donate/
[:recommend]: http://www.workingwithrails.com/person/7739-evan-weaver
[:aspell]: http://www.aspell.net
[:aspell_options]: http://aspell.net/man-html/The-Options.html
[:forum]: http://rubyforge.org/forum/forum.php?forum_id=13988
[:additional_resource1]: http://blog.evanweaver.com/articles/2007/03/10/add-gud-spelning-to-ur-railz-app-or-wharever