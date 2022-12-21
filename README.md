# Static website to S3 Github action
> This action will deploy your static website to S3 without the html extension.

I tested only with NextJS exported website, but I don't see any reason why it shouldn't work
with other setups. If it's not working for you, [please report an issue](https://github.com/eisberg-labs/static-website-to-s3/issues).

## Prerequisite

You have configured your S3 bucket for [static website hosting](https://www.amarjanica.com/host-a-nextjs-static-website-on-s3#Configure_S3_Bucket_for_static_website_hosting).

## Usage

Define AWS_DEFAULT_REGION, AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY environment variables.
This action should be run after the static website is built:

```yaml
 - name: Deploy to s3
   uses: eisberg-labs/static-website-to-s3@main
   with:
     target: nextjs-testapp/out
     dest: next-to-s3/nextjs-testapp
     exclusions: ^nextjs-testapp\/out\/(index|404).html$
     bucket: ${{ secrets.BUCKET }}
```

## Example

There's an example action at [Actions](https://github.com/eisberg-labs/static-website-to-s3/actions),
and [configuration file](.github/workflows/deploy-nextjs.yml) testing the NextJS build.


## License
MIT © [Eisberg Labs](http://www.eisberg-labs.com)
