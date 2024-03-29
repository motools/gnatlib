GNATlib
=======

About
-----

This is a python library version of the [GNAT software](https://github.com/motools/gnat)

Perform a track lookup on the Musicbrainz database, using
embedded ID3 tags or manually supplied metadata and the
disambiguation algorithm from Raimond et al. 2008

    Copyright (C) 2009  Yves Raimond, Kurt Jacobson

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <http://www.gnu.org/licenses/>

  Yves Raimond, C4DM, Queen Mary, University of London
  yves.raimond (at) elec.qmul.ac.uk
  kurt.jacobson (at) elec.qmul.ac.uk

Requirements
------------

 * musicbrainz2 - http://musicbrainz.org/doc/PythonMusicBrainz2
 * mutagen - easy_install mutagen

Installation
------------

$ python setup.py install

Usage
-----

>> import gnatlib
>> result = gnatlib.filelookup('test.mp3')
20.04.09 17:11:34 DEBUG     - Trying to guess an ID for track "Light My Fire", artist "Jay Dee", release "Donuts", track number 4
20.04.09 17:11:34 DEBUG    ID Found !
>> result['artistURI']
u'http://musicbrainz.org/artist/cbcbb22c-3a8d-46af-b4ba-09c98f0d7931'

>> gnatlib.metadatalookup(artist='Jay Dee', release='Donuts')
20.04.09 17:21:07 DEBUG     - Trying to guess an ID for track "None", artist "Jay Dee", release "Donuts", track number None
20.04.09 17:21:07 DEBUG    ID Found !

{'artist': <musicbrainz2.model.Artist object at 0x1b0e410>,
 'artistMbz': u'http://musicbrainz.org/artist/cbcbb22c-3a8d-46af-b4ba-09c98f0d7931',
 'artistURI': u'http://dbtune.org/musicbrainz/resource/artist/cbcbb22c-3a8d-46af-b4ba-09c98f0d7931',
 'releaceMbz': u'http://musicbrainz.org/release/e3655e9f-3db1-434d-bb4b-3529d09b2989',
 'release': <musicbrainz2.model.Release object at 0x19bcad0>,
 'releaseURI': u'http://dbtune.org/musicbrainz/resource/release/e3655e9f-3db1-434d-bb4b-3529d09b2989',
 'score': 88,
 'track': None}

Notice this actually returns the more accurate result for 'J-Dilla' the pseudonym
used by Jay Dee when the album 'Donuts' was released.

Known Issues
------------

* 2009-20-04
	* @param use_cache=False does not seem to work correctly - sorry you've got to use the cache for now...
	* turning off verbose seems to not work :-/
	* no clean up of the ./cache directory - you have to do this yourself
	* we use dbtune.org/musicbrainz URIs - it is not clear this is best
	* no support for PUID MusicDNS lookup

PS
--

The [old project repository location at SourceForge](http://motools.svn.sourceforge.net/viewvc/motools/gnatlib/) is now deprecated. All new developments will be pushed to this repository location here at GitHub.
