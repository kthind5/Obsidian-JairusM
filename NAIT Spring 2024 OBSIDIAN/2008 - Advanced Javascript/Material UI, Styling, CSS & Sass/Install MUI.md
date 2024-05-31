```table-of-contents
```
[MUI Website](https://mui.com/material-ui/getting-started/installation/)
# 1. Terminal Command
```bash
npm install @mui/material @emotion/react @emotion/styled
```


# 2. Install Roboto Font
Material UI uses the [Roboto](https://fonts.google.com/specimen/Roboto) font by default. Add it to your project via Fontsource, or with the Google Fonts CDN.

```bash
npm install @fontsource/roboto
```

Then you can import it in your entry point like this:
`Do this in the app.js file`
`Delete the imported styles.css that is on top`

```tsx
import '@fontsource/roboto/300.css';
import '@fontsource/roboto/400.css';
import '@fontsource/roboto/500.css';
import '@fontsource/roboto/700.css';
```


# 3. Icons (If required in assignment)
To use the [font Icon component](https://mui.com/material-ui/icons/#icon-font-icons) or the prebuilt SVG Material Icons (such as those found in the [icon demos](https://mui.com/material-ui/icons/)), you must first install the [Material Icons](https://fonts.google.com/icons?icon.set=Material+Icons) font. You can do so with npm, or with the Google Web Fonts CDN.


```bash
npm install @mui/icons-material
```