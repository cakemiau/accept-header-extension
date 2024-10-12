Many web servers detect WebP compatibility via the `Accept` header sent by
browsers. When a browser supports this format, it usually tells the site
by including `image/webp` in the accept header.

Some sites only serve WebP images to WebP-compatible browsers by reading this header.
However, this approach doesn't provide a way of retrieving the non-WebP version
of the image because this header is not usually modifiable by the user.

Another drawback of WebP is that they're usually generated from an already lossy format like JPG,
meaning they always have worse overall quality than their JPG counterparts, and the format is barely
supported by other software.

To prevent this, this browser extension overwrites the following:

#### Firefox ([Get the extension](https://addons.mozilla.org/firefox/addon/accept-header-override/))

|          | `Accept` for images                                                     |
| -------- | ----------------------------------------------------------------------- |
| Default  | `image/avif,image/webp,image/png,image/svg+xml,image/*;q=0.8,*/*;q=0.5` |
| Modified | `image/png,image/jpeg,image/svg+xml,image/*;q=0.8,*/*;q=0.5`            |

|          | `Accept` for pages                                                                                              |
| -------- | --------------------------------------------------------------------------------------------------------------- |
| Default  | `text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/png,image/svg+xml,*/*;q=0.8` |
| Modified | `text/html,application/xhtml+xml,application/xml;q=0.9,image/png,image/jpeg,image/svg+xml,*/*;q=0.8`            |

#### Chrome

> [!NOTE]
> The Chrome Web Store requires a payment of a fee to be able to submit extensions.
> Since this is just a silly extension, I won't be uploading it there unless I want
> to publish a more elaborated extension in the future.

|          | `Accept` for images                                                |
| -------- | ------------------------------------------------------------------ |
| Default  | `image/avif,image/webp,image/apng,image/svg+xml,image/*,*/*;q=0.8` |
| Modified | `image/png,image/jpeg,image/apng,image/svg+xml,image/*,*/*;q=0.8`  |

|          | `Accept` for pages                                                                                                                        |
| -------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Default  | `text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7` |
| Modified | `text/html,application/xhtml+xml,application/xml;q=0.9,image/png,image/jpeg,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7`  |

---

> [!NOTE]
> If your browser keeps getting WebP images, the site may be using the `<picture>` HTML tag,
> in this case you can just use the Inspect tool to find the URL of the image in a different format.

> [!NOTE]
> Please note that this extension will only work on websites that use the Accept header to
> detect WEBP compatibility. It will not work on websites that always serve this format or
> that use other means, such as User Agent, to detect compatibility.
