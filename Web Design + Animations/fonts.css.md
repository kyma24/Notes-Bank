-   fonts.css
    
    ```html
    <script src="<https://gist.github.com/sarthaktexas/aa75ee8d52aedaf41fbb5d1caaf9ea04.js>"></script>
    ```
    
    ```css
    @font-face {
      font-family: 'Bolden';
      src: url("<https://dcs7zyl28wkldban.s3.amazonaws.com/angelhacks/697286601725968436/Bolden-Display_Hust.otf>") format("opentype");
    }
    
    @font-face {
    font-family: 'Anton';
    font-style: normal;
    font-weight: 400;
    font-display: swap;
    src: url(<https://fonts.gstatic.com/s/anton/v15/1Ptgg87LROyAm3K9-C8CSKlvPfE.woff2>) format('woff2');
    unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB, U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
    }
    
    @font-face {
    font-family: 'Anton';
    font-style: normal;
    font-weight: 400;
    font-display: swap;
    src: url(<https://fonts.gstatic.com/s/anton/v15/1Ptgg87LROyAm3Kz-C8CSKlv.woff2>) format('woff2');
    unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
    }
    
    @font-face {
    font-family: 'Shrikhand';
    font-style: normal;
    font-weight: 400;
    font-display: swap;
    src: url(<https://fonts.gstatic.com/s/shrikhand/v6/a8IbNovtLWfR7T7bMJwrDYKR8Ttcte1q.woff2>) format('woff2');
    unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB, U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
    }
    
    @font-face {
    font-family: 'Shrikhand';
    font-style: normal;
    font-weight: 400;
    font-display: swap;
    src: url(<https://fonts.gstatic.com/s/shrikhand/v6/a8IbNovtLWfR7T7bMJwrA4KR8TtctQ.woff2>) format('woff2');
    unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
    }
    
    @font-face {
    font-family: 'Fira Code';
    font-style: normal;
    font-weight: 500;
    font-display: swap;
    src: url(<https://fonts.gstatic.com/s/firacode/v10/uU9eCBsR6Z2vfE9aq3bL0fxyUs4tcw4W_A9sJV77MOzlojwUKaJO.woff>) format('woff');
    unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB, U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
    }
    
    @font-face {
    font-family: 'Fira Code';
    font-style: normal;
    font-weight: 500;
    font-display: swap;
    src: url(<https://fonts.gstatic.com/s/firacode/v10/uU9eCBsR6Z2vfE9aq3bL0fxyUs4tcw4W_A9sJVD7MOzlojwUKQ.woff>) format('woff');
    unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
    }
    
    @font-face {
    font-family: 'Nunito';
    font-style: normal;
    font-weight: 900;
    font-display: swap;
    src: url(<https://fonts.gstatic.com/s/nunito/v16/XRXW3I6Li01BKofAtsGUb-vIWzgPDEtj.woff2>) format('woff2');
    unicode-range: U+0100-024F, U+0259, U+1E00-1EFF, U+2020, U+20A0-20AB, U+20AD-20CF, U+2113, U+2C60-2C7F, U+A720-A7FF;
    }
    
    @font-face {
    font-family: 'Nunito';
    font-style: normal;
    font-weight: 900;
    font-display: swap;
    src: url(<https://fonts.gstatic.com/s/nunito/v16/XRXW3I6Li01BKofAtsGUYevIWzgPDA.woff2>) format('woff2');
    unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
    }
    
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
    
    .bg-coral {
    background-color: #ECBBBB;
    }
    
    .bolden {
    font-family: 'Bolden', sans-serif;
    text-transform: uppercase;
    }
    
    .anton {
    font-family: 'Anton', sans-serif;
    text-transform: uppercase;
    }
    
    .text-brown {
    color: #3D1A07;
    }
    
    .bg-yellow {
    background: #F6F8B9;
    }
    
    .shrikhand {
    font-family: 'Shrikhand', sans-serif;
    text-transform: uppercase;
    }
    
    .bg-mint {
    background: #89F4CE;
    }
    
    .nunito {
    font-family: 'Nunito', sans-serif;
    }
    
    .firacode {
    font-family: 'Fira Code', sans-serif;
    }
    
    .number-border {
    border: 12px solid black;
    }
    ```