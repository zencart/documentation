Introduction
============

The Request class is meant to replace direct references to the Super Global $_GET, $_POST etc. arrays. 
It is based on https://github.com/auraphp/Aura.Web

It is instantiated in the Global namespace as $zcRequest, and provides the following methods.

### get

    public function get($param, $default = null, $source = 'get')

### readGet

    public function readGet($param, $default = null)

### readPost

    public function readPost($param, $default = null)

### has

    public function has($param, $source = 'get')

### all

    public function all($source = 'get')


