## CÀI ĐẶT TYPESCRIPT CHO REACTJS

**Bước 1:** Cài đặt TypeScript, `ts-loader` và `source-map-loader` để webpack có thể biên dịch TS thành JS.
```powershell
  npm install --save-dev typescript ts-loader source-map-loader
```

**Bước 2:** Cài đặt các file định nghĩa kiểu dữ liệu từ `@types` để các thư viện trong project có thể sử dụng.
```powershell
  npm install --save @types/react @types/react-dom
```

**Bước 3:** Cấu hình TS bằng file `tsconfig.json`
```json
  {
      "compilerOptions": {
          "outDir": "./dist/",        // path to output directory
          "sourceMap": true,          // allow sourcemap support
          "strictNullChecks": true,   // enable strict null checks as a best practice
          "module": "es6",            // specify module code generation
          "jsx": "react",             // use typescript to transpile jsx to js
          "target": "es5",            // specify ECMAScript target version
          "allowJs": true             // allow a partial TypeScript and JavaScript codebase

      },
      "include": [
          "./src/"
      ]
  }
```

**Bước 4:** Cấu hình webpack để có thể build song song JS và TS
```js
module.exports = {
  // change to .tsx if necessary
  entry: './src/app.jsx',
  output: {
    filename: './bundle.js'
  },
  resolve: {
    // changed from extensions: [".js", ".jsx"]
    extensions: [".ts", ".tsx", ".js", ".jsx"]
  },
  module: {
    rules: [
      // changed from { test: /\.jsx?$/, use: { loader: 'babel-loader' }, exclude: /node_modules/ },
      { test: /\.(t|j)sx?$/, use: { loader: 'ts-loader' }, exclude: /node_modules/ },

      // addition - add source-map support
      { enforce: "pre", test: /\.js$/, exclude: /node_modules/, loader: "source-map-loader" }
    ]
  },
  externals: {
    "react": "React",
    "react-dom": "ReactDOM",
  },
  // addition - add source-map support
  devtool: "source-map"
}
```