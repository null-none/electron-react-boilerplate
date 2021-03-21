## Minimal Electron, React and Webpack boilerplate

Minimal Electron, React, PostCSS and Webpack boilerplate to help you get started with building your next app.

### Install

#### Install dependencies

```
npm install
```
or
```
yarn
```

### Usage

#### Run the app

```
npm run start
```
or
```
yarn start
```

#### Build the app (automatic)

```
npm run package
```
or
```
yarn package
```

#### Build the app (manual)

```
npm run build
```
or
```
yarn build
```

#### Test the app (after `npm run build` || `yarn run build`)
```
npm run prod
```
```
yarn prod
```

### Add Sass

Adding Sass to boilerplate requires updating webpack configs and adding necessary loaders.

1) To `webpack.build.config.js` and `webpack.dev.config.js` add new object to `rules`:

```JavaScript
{
  test: /\.scss$/,
  use: [
    { loader: 'style-loader' },
    { loader: 'css-loader' },
    { loader: 'sass-loader' }],
  include: defaultInclude
}
```

2) Install additional loaders for sass, `sass-loader` and `node-sass`.

3) Rename all CSS file to `.scss`.

### Change app title

This boilerplate uses [HTML Webpack Plugin](https://github.com/jantimon/html-webpack-plugin#options) to generate the HTML file of the app. Changing app title is possible only through webpack configs, `webpack.build.config.js` and `webpack.dev.config.js`. App title can be changed by adding objects of options.

In `webpack.build.config.js`:

```JavaScript
plugins: [
  new HtmlWebpackPlugin({title: 'New app title '}),// Add this (line 41)
  new MiniCssExtractPlugin({
    // Options similar to the same options in webpackOptions.output
    // both options are optional
    filename: 'bundle.css',
    chunkFilename: '[id].css'
  }),
  new webpack.DefinePlugin({
    'process.env.NODE_ENV': JSON.stringify('production')
  }),
  new BabiliPlugin()
],
```

In `webpack.dev.config.js`:

```JavaScript
plugins: [
  new HtmlWebpackPlugin({title: 'New app title '}),// Add this (line 36)
  new webpack.DefinePlugin({
    'process.env.NODE_ENV': JSON.stringify('development')
  })
],
```