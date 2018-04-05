Libcloud
=========

Using the libcloud compute driver for Slipstream
-------------------------------------------------
For the browser-based interfaces to Nuvla and Onedata services, you can directly
use the credentials for your Identity Provider in the eduGAIN and Elixir AAI federations.
For API and command line interface access to Nuvla, the use of revocable API key/secret pairs are recommended.

### Generating API key/secret on Nuvla

- Define the following alias::

  $ alias ss-curl="curl --cookie-jar ~/cookies -b ~/cookies -sS"

- Create a json file defining the nuvla session with your <username> and <password>::

    cat > session-create-internal.json <<EOF
    {
      "sessionTemplate" : {
                            "href" : "session-template/internal",
                            "username" : "<username>",
                            "password" : "<password>"
                           }
    }
    EOF

- Generate a `cookies` file for the session::

     ss-curl https://nuv.la/api/session \
         -D - \
         -o /dev/null \
         -XPOST \
         -H content-type:application/json \
         -d@session-create-internal.json

- You may check that a `cookies` file is actually created::

  $ cat ~/cookies

- Credential Creation::

    cat > create.json <<EOF
    {
      "credentialTemplate" : {
                               "href" : "credential-template/generate-api-key",
                               "ttl" : 86400
                              }
    }
    EOF

NB : The ttl parameter for the API key/secret lifetime (TTL) is optional.
If not provided, the credential will not expire (but can still be revoked at anytime.)
The TTL value is in seconds, so the above time corresponds to 1 day.

To actually create the new credential::

  $ ss-curl https://nuv.la/api/credential \
   -X POST \
   -H 'content-type: application/json' \
   -d @create.json
  {
    "status" : 201,
    "message" : "created credential/05797630-c1e2-488b-96cd-2e44acc8e286",
    "resource-id" : "credential/05797630-c1e2-488b-96cd-2e44acc8e286",
    "secretKey" : "..."
  }
  
Note carefully the secret (secretKey) that is returned from the server.
The “key” is the value of “resource-id”. This secret is not stored on the server and cannot be recovered.


### Using Libcloud for Nuvla deployment

Using Libcloud directly on Advania, Exoscale, OTC
-------------------------------------------------