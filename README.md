# inject-body-compaticity-webpack-plugin Introduction
A [HTML Webpack Plugin](https://github.com/jacksplwxy/html-webpack-plugin)  that injects a custom string into the body of the html-webpack-plugin output.It is compatible with different versions of WebPack and HtmlWebPackPlugin. (inspired by [inject-body-webpack-plugin](https://github.com/Jaid/inject-body-webpack-plugin))


<br>

# Differences with inject-body-webpack-plugin
* It is compatible with different versions of WebPack and HtmlWebPackPlugin.
* It can work according to process.env.NODE_ENV.

<br>

# Installation

```bash
npm i -D inject-body-compaticity-webpack-plugin
```

<br>

# Example

### Input

**webpack.config.js**

```js
import HtmlWebpackPlugin from "html-webpack-plugin"
import InjectBodyCompaticityWebpackPlugin from "inject-body-compaticity-webpack-plugin"

export default {
  mode: 'development',
  plugins: [
    new HtmlWebpackPlugin(),
    new InjectBodyCompaticityWebpackPlugin({
      position:'start',
      content: '<script>alert("Hello InjectBodyCompaticityWebpackPlugin!")</script>',
      env: ["development"]
    }),
  ],
}
```


### Output

**index.html**

```html
<html><body><script>alert("Hello InjectBodyCompaticityWebpackPlugin!")</script></body></html>
```


<br>

# Options
<table>
<tr>
<th></th>
<th>Type</th>
<th>Default</th>
<th>Info</th>
</tr>
<tr>
<td>position</td>
<td>string</td>
<td>start</td>
<td>If “start”, the content will be injected as close to the body opening tag as possible. If “end”, the content will be injected as close to the body ending tag as possible.</td>
</tr>
<tr>
<td>content</td>
<td>string</td>
<td>""</td>
<td>The text that will be injected into the final HTML output.</td>
</tr>
<tr>
<td>env</td>
<td>string[]</td>
<td>[]</td>
<td>When the value of process.env.NODE_ENV is in the list, the plugin will take effect</td>
</tr>
</table>

