Introduction
============

The Request class is meant to replace direct references to the Super Global $_GET, $_POST etc. arrays. 
It is based on [Aura.Web](https://github.com/auraphp/Aura.Web)

It is instantiated in the Global namespace as $zcRequest, and provides the following methods.

### get

    public function get($param, $default = null, $source = 'get')
    
#### $param required string
The parameter to get

#### $default optional mixed
If the parameter does not exist, then return this default value

#### $source optional string
The superglobal to query, either `get` or `post`.


### readGet

    public function readGet($param, $default = null)
    
An alias to the get function where the source = 'get'    

### readPost

    public function readPost($param, $default = null)

An alias to the get function where the source = 'post'    

### has

    public function has($param, $source = 'get')
    
*DEPRECATED*

### all

    public function all($source = 'get')

#### $source optional string
The superglobal to query, either `get` or `post`.

