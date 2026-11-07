<p align="center"><img src="BlazorWasm.MelodicJourneysOfCollin/wwwroot/logo.svg" alt="Collin Radio turntable logo" width="96" height="96" /></p>

# Melodic Journeys of Collin (Collin Radio)

Collin ရဲ့ Music Catalog ကို ရှာဖွေနားထောင်နိုင်ပြီး Favorites နဲ့ DJ Room ပါဝင်တဲ့ **.NET 8 Blazor WebAssembly Project** ပါ။ [App ကို ဒီမှာ ဖွင့်နိုင်ပါတယ်](https://burma-collin.vercel.app/)။

[Burma Project Ideas](https://github.com/burma-project-ideas) အောက်မှာ နောက်လာမယ့်သူတွေ App Flow ကို လေ့လာပြီး ကိုယ်နှစ်သက်တဲ့ Programming Language နဲ့ ပြန်ရေးကြည့်နိုင်ဖို့ ထားပေးထားတာပါ။ App က Browser ထဲမှာ အလုပ်လုပ်ပြီး Account နဲ့ Server Database မလိုပါဘူး။ Favorites နဲ့ Theme ကို ဒီ Browser ထဲမှာ သိမ်းထားပါတယ်။

## အဓိက ပံ့ပိုးသူများနှင့် မူရင်း Data

| ပံ့ပိုးသူ / ရင်းမြစ် | ပါဝင်သည့်အပိုင်း |
| --- | --- |
| Collin နှင့် Catalog ထဲက ပူးပေါင်းဖန်တီးသူများ | Music tracks၊ Remix နဲ့ မူရင်း Artwork များ |
| [Sann Lynn Htun](https://github.com/sannlynnhtun-coding) | မူရင်း Blazor WebAssembly Project နဲ့ App implementation |
| [PrebuiltUI](https://prebuiltui.com/) | လက်ရှိ UI ရဲ့ Typography၊ Grid၊ Pill Buttons နဲ့ Color Treatment အတွက် Design Reference |
| Inter | Self-hosted Font; License ကို `wwwroot/fonts/Inter-LICENSE` မှာ ဖတ်နိုင်ပါတယ် |

Repository ကို Organization ဆီ ရွှေ့ထားခြင်းက မူရင်းဖန်တီးသူများရဲ့ Credit နဲ့ Music/Artwork ပိုင်ဆိုင်မှုကို မပြောင်းလဲပါဘူး။ Catalog နဲ့ Artwork Links တွေကို လက်ရှိ Project ထဲကအတိုင်း ထိန်းသိမ်းထားပါတယ်။ ဒီ Repository မှာ Project တစ်ခုလုံးအတွက် License ဖိုင် မပါသေးတဲ့အတွက် ပြန်လည်ဖြန့်ဝေမယ်ဆိုရင် သက်ဆိုင်ရာဖန်တီးသူရဲ့ ခွင့်ပြုချက်ကို စစ်ဆေးပါ။

## အသုံးပြုပုံ

1. **Discover (`/`)** မှာ Collections နဲ့ Tracks ကို ကြည့်ပြီး သီချင်းရွေးပါ။
2. **Releases (`/releases`)** မှာ Track၊ Artist၊ Genre နဲ့ Collection အမည်အလိုက် ရှာပြီး Play လုပ်နိုင်ပါတယ်။
3. **Albums (`/albums`)** မှာ Collection ကို တစ်ခုလုံး ဖွင့်နိုင်ပြီး Detail Page မှာ Track List ကြည့်နိုင်ပါတယ်။
4. Heart ကို နှိပ်ထားတဲ့ Tracks တွေကို **Favorites (`/favorites`)** မှာ ပြန်ရှာနိုင်ပါတယ်။ Account မလိုဘဲ ဒီ Browser ထဲမှာ သိမ်းထားပါတယ်။
5. **DJ Room (`/dj`)** မှာ Turntable၊ Queue၊ Previous/Next၊ Seek နဲ့ Volume Controls ကို အသုံးပြုနိုင်ပါတယ်။ ဒီ Page က သီးခြား Audio Mixer မဟုတ်ဘဲ App နဲ့ မျှဝေသုံးထားတဲ့ Player ကို ဖော်ပြထားတာပါ။
6. Header က Theme Button နဲ့ System၊ Light၊ Dark ကို ပြောင်းနိုင်ပါတယ်။ Page ပြောင်းသွားလည်း Audio Player က ဆက်နားထောင်နိုင်ပါတယ်။

## App ရဲ့ Workflow

### ၁။ Catalog နဲ့ Browser State ကို ဖတ်မယ်

`Program.cs` က Player၊ Library နဲ့ Theme Services တွေကို Register လုပ်ပါတယ်။ `MusicService.LocalPlaylist` က `MusicService.cs` ထဲက `JsonData.LocalPlaylist` ကို ဖတ်ပြီး `AnnotateAlbums` နဲ့ Collection အုပ်စုခွဲပါတယ်။ `MainLayout.razor` က Favorites နဲ့ Theme State ကို Initialize လုပ်ပါတယ်။

### ၂။ ရှာဖွေပြီး Collection ရွေးမယ်

Home နဲ့ Releases က Track Name၊ Artist၊ Genre၊ Album Title ကို Case-insensitive Search လုပ်ပါတယ်။ Albums က တူညီတဲ့ Catalog ကို Collection အလိုက် ပြပါတယ်။ Search နဲ့ Route ပြောင်းခြင်းက သိမ်းထားတဲ့ Favorites ကို မပြောင်းလဲပါဘူး။

### ၃။ Shared Player နဲ့ နားထောင်မယ်

Track Card က `PlayerStateService.PlayTrack`၊ Collection က `PlayQueue` ကို ခေါ်ပါတယ်။ Queue မှာ Link တူတဲ့ Tracks တွေကို Deduplicate လုပ်ပါတယ်။ `GlobalAudioHost.razor` က HTML Audio Element တစ်ခုနဲ့ Playback၊ Timeline၊ Volume နဲ့ Seek ကို JavaScript မှတစ်ဆင့် ချိတ်ဆက်ပါတယ်။ Audio File Path က `music/{Link}` ဖြစ်ပြီး Artwork တချို့ကို ပြင်ပ URL ကနေ ဖတ်ပါတယ်။

### ၄။ Favorites နဲ့ Theme ကို သိမ်းမယ်

`LibraryStateService` က Favorite Track Links ကို `collin-favorites` Local Storage Key နဲ့ သိမ်းပါတယ်။ `ThemeService` နဲ့ `wwwroot/js/app.js` က `collin-theme` ကို သုံးပါတယ်။ Track ကို Unfavorite လုပ်ရင် Favorites Page နဲ့ Count ကို ချက်ချင်း Refresh လုပ်ပါတယ်။ Browser/Profile/Domain ပြောင်းရင် ဒီ State က အလိုအလျောက် Sync မဖြစ်ပါဘူး။

## Data ကို လေ့လာမယ်

- Active Catalog: `BlazorWasm.MelodicJourneysOfCollin/Services/MusicService.cs` ထဲက `JsonData.LocalPlaylist`။
- Track Model: `Models/MusicInfoModel.cs` — Name၊ Artists၊ Genre၊ Link၊ Cover၊ Length နဲ့ Album Metadata။
- Collection Model: `Models/AlbumCollectionModel.cs`။
- `wwwroot/data/music_data.json` လည်း ရှိပေမယ့် လက်ရှိ Active Pages ရဲ့ အဓိက Catalog Source က `MusicService.LocalPlaylist` ပါ။
- UI ထဲက Track Length က Catalog Metadata ဖြစ်ပြီး Player Duration က Audio File ကနေ ဖတ်တာပါ။ တချို့ Metadata နဲ့ Audio Duration ကွာနိုင်ပါတယ်။

## Project ဖွဲ့စည်းပုံ

| Path | တာဝန် |
| --- | --- |
| `BlazorWasm.MelodicJourneysOfCollin/Pages/` | Discover၊ Releases၊ Albums၊ Favorites၊ DJ Room နဲ့ Artist Pages |
| `Components/` | Track Card၊ Favorite Button၊ Shared Player၊ Logo နဲ့ Audio Host |
| `Layout/` | Header၊ Responsive Navigation၊ Footer နဲ့ Shared Audio Layout |
| `Services/` | Music Catalog၊ Player State၊ Favorites နဲ့ Theme |
| `Styles/app.css`, `Styles/modern.css` | Tailwind Source နဲ့ လက်ရှိ Design Styles |
| `wwwroot/` | Compiled CSS၊ JavaScript၊ Fonts၊ Logo၊ Icons နဲ့ Music Files |
| `screenshots/` | Live App ရဲ့ Design Previews |
| `.github/workflows/deploy.yml` | Build Checks နဲ့ Vercel Production Deployment |

App ထဲက Short Paths တွေက `BlazorWasm.MelodicJourneysOfCollin/` အောက်ကို ရည်ညွှန်းပါတယ်။

## Local မှာ Run မယ်

.NET 8 SDK၊ Node.js 24 နဲ့ Git လိုအပ်ပါတယ်။

```sh
git clone https://github.com/burma-project-ideas/melodic-journeys-of-collin.git
cd melodic-journeys-of-collin
npm ci
npm run build:css
dotnet run --project BlazorWasm.MelodicJourneysOfCollin/BlazorWasm.MelodicJourneysOfCollin.csproj --launch-profile http
```

[http://localhost:5182](http://localhost:5182) ကို ဖွင့်ပါ။ CSS ပြင်နေချိန်မှာ သီးခြား Terminal တစ်ခုက `npm run watch:css` ကို Run နိုင်ပါတယ်။

## Build နဲ့ Deployment

```sh
npm run build:css
dotnet build BlazorWasm.MelodicJourneysOfCollin/BlazorWasm.MelodicJourneysOfCollin.csproj -c Release
dotnet publish BlazorWasm.MelodicJourneysOfCollin/BlazorWasm.MelodicJourneysOfCollin.csproj -c Release -o artifacts/publish
```

Published Static App က `artifacts/publish/wwwroot/` ထဲမှာ ရှိပါတယ်။ GitHub Actions က Pull Request တွေမှာ Build စစ်ပြီး `master` Push နဲ့ Manual Run တွေမှာ **Vercel Build Output API** Format ကို ပြင်ဆင်ကာ `burma-collin` Project ဆီ Deploy လုပ်ပါတယ်။ Static File တွေကို အရင် Serve ပြီး Client-side Route တွေကို `index.html` ဆီ Fallback လုပ်ပါတယ်။

Repository Secrets မှာ `VERCEL_TOKEN`၊ `VERCEL_ORG_ID` နဲ့ `VERCEL_PROJECT_ID` လိုပါတယ်။ Token Value ကို Source Code ထဲ မထည့်ပါနဲ့။ Production Link က [burma-collin.vercel.app](https://burma-collin.vercel.app/) ပါ။

## စစ်ဆေးမယ်

- `npm run build:css` နဲ့ Release Build အောင်မြင်ရပါမယ်။
- Search Result၊ Empty State၊ Track Play/Pause၊ Queue Selection၊ Seek နဲ့ Volume ကို စမ်းပါ။
- Favorite Save/Remove၊ Reload ပြီး State ကျန်ရှိမှုနဲ့ Light/Dark Theme ကို စမ်းပါ။
- Desktop/Mobile မှာ Overflow မရှိတာနဲ့ `/albums`၊ `/releases`၊ `/favorites`၊ `/dj` ကို တိုက်ရိုက်ဖွင့်နိုင်တာ စစ်ပါ။
- App Shell က Service Worker Cache သုံးတာကြောင့် Update အဟောင်းပဲ မြင်ရရင် Tab ကို ပိတ်ပြီး ပြန်ဖွင့်ပါ။ Favorites ကို ထိန်းထားချင်ရင် Site Data ကို မရှင်းပါနဲ့။

## ကိုယ်တိုင် ပြန်ရေးကြည့်ချင်ရင်

Catalog ဖတ်ခြင်း → Collection ခွဲခြင်း → Track ရှာခြင်း → Shared Audio Playback → Favorites သိမ်းခြင်း ဆိုတဲ့ Flow ကို ကိုယ်နှစ်သက်တဲ့ Language နဲ့ ပြန်ရေးကြည့်နိုင်ပါတယ်။ Audio State ကို Page တစ်ခုချင်းထဲမှာ မထားဘဲ Shared Service ထဲမှာထားပုံကို လေ့လာနိုင်ပါတယ်။

## ပါဝင်ကူညီမယ်

Bug Report၊ Documentation၊ Accessibility နဲ့ Metadata ပြင်ဆင်မှုတွေကို Issue / Pull Request နဲ့ ပံ့ပိုးနိုင်ပါတယ်။ Music နဲ့ Artwork ပြောင်းလဲမယ်ဆိုရင် မူရင်း Creator Credit နဲ့ Source Link ကို ထည့်ပေးပါ။ Design Reference နဲ့ Inter Font License ကို ဆက်လက်ထိန်းသိမ်းပါ။

## Screenshots

Captured from the [live app](https://burma-collin.vercel.app/).

### Light theme

![Collin Radio light theme with gradient headline and floating music player](screenshots/home-light.jpg)

### Dark theme

![Collin Radio dark theme with the new turntable logo and music player](screenshots/home-dark.jpg)

### DJ Room

A dedicated turntable, playback controls, readable session queue, and collection shortcuts.

![Redesigned Collin DJ Room](screenshots/dj-room.jpg)

### Albums

Collections use the DJ Room typography, artwork cards, and direct playback controls.

![Redesigned Collin Albums page](screenshots/albums.jpg)

### Releases

Searchable track cards match Albums and the DJ Room, with favorites, playback, and collection links.

![Redesigned Collin Releases page](screenshots/releases.jpg)

### Favorites

Saved tracks share the Releases cards. A new empty state links to discovery, and removing favorites updates the library immediately.

![Redesigned Collin Favorites page](screenshots/favorites.jpg)
