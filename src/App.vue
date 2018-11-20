<template>
  <div id="app"
       class="h-screen flex justify-center bg-grey-light">
    <div class="w-full md:w-5/6 h-full bg-white overflow-y-auto">

      <ul class="py-4 flex justify-around items-center list-reset">
        <!-- <li class="cursor-pointer"
            @click="selected = 'photos'">
          Photos
        </li>
        <li class="cursor-pointer"
            @click="selected = 'cards'">
          Components
        </li>
        <li class="cursor-pointer"
            @click="selected = 'columns'">
          Photos-Columns
        </li>
        <li class="cursor-pointer"
            @click="selected = 'columns-el'">
          Components-Columns
        </li> -->
        <li class="cursor-pointer"
            @click="selected = 'numbers'">
          Numbers
        </li>
        <li class="cursor-pointer"
            @click="selected = 'columns-numbers'">
          Numbers-Columns
        </li>
      </ul>

      <div v-show="selected === 'numbers'">
        <div class="test -mx-2">
          <div v-for="number in numbers"
               :key="number"
               class="bg-green-dark border border-grey p-4 m-2"
               v-text="number" />
        </div>
      </div>

      <div v-show="selected === 'columns-numbers'">
        <numbers-gallery :numbers="numbers" />
      </div>
      <!-- <div v-show="selected === 'columns'">
        <div class="test">
          <img v-for="photo in photos"
               :key="photo.id"
               :src="photo.small" />
        </div>
      </div>
      <div v-show="selected === 'columns-el'">
        <div class="test -m-4">
          <div v-for="(photo, index) in photos"
               :key="photo.id + index"
               class="flex flex-col m-4 p-2 border">
            <h4><a :href="photo.regular"
                 target="_blank">
                {{photo.id}}
              </a> </h4>
            <img class="my-2"
                 :src="photo.thumb" />
            <p>{{photo.description}}</p>
          </div>
        </div>
      </div> -->

      <!-- <div v-show="selected === 'photos'">
        <photo-gallery :photos="photos" />
      </div>

      <div v-show="selected === 'cards'">
        <component-gallery :photos="photos" />
      </div> -->
    </div>
  </div>
</template>

<script>
import PhotoGallery from "./components/tests/PhotoGallery";
import ComponentGallery from "./components/tests/ComponentGallery";
import NumbersGallery from "./components/tests/NumbersGallery";

import photos from "./photos.js";

export default {
  name: "app",
  components: {
    PhotoGallery,
    ComponentGallery,
    NumbersGallery
  },
  data() {
    return {
      selected: "numbers",
      numbers: [
        "1 - Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer at laoreet dolor, vitae pretium est. Donec iaculis elit felis, nec mollis erat pulvinar vel. Ut dignissim ex sed ante scelerisque, at blandit massa facilisis. Duis accumsan non nisi ac accumsan. Aenean in faucibus augue, nec imperdiet quam. Nullam non justo mi. Donec eleifend venenatis ante, eget euismod sapien tempus eu. Vestibulum nulla ipsum, volutpat et orci ac, consectetur cursus tortor. Suspendisse tristique lectus vel neque interdum pulvinar at eu nibh. Phasellus sed nulla augue.    ",
        "2 - Nam sollicitudin arcu augue, vel pulvinar felis tincidunt at. Ut tempor id lorem ac imperdiet. Proin ut eros dapibus, rhoncus leo eget, vehicula lacus. Sed et ex et turpis hendrerit dictum. Phasellus dictum nibh vitae viverra tristique. Aenean dapibus dictum velit, ac efficitur tortor consectetur sit amet. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Etiam sapien nisi, iaculis at posuere eu, imperdiet vitae sem. Ut pharetra turpis augue, eu maximus nunc congue ut. Curabitur in congue turpis. Praesent vel lobortis elit. Sed ac sodales nisi. In hac habitasse platea dictumst.    ",
        "3 - Nulla hendrerit lectus mi. Aliquam erat volutpat. Fusce tristique dolor eget tellus blandit varius. Proin et nunc pharetra, elementum tortor nec, imperdiet felis. Proin vitae arcu erat. Sed maximus quis quam vitae tristique. Ut tempus velit justo, id posuere nulla luctus id. Vestibulum quis urna id dolor eleifend gravida in at elit.    ",
        "4 - Interdum et malesuada fames ac ante ipsum primis in faucibus. Nulla cursus eros eget elit tempus, in cursus tortor tempus. Curabitur quis volutpat mauris. Vivamus posuere orci id lectus condimentum, sit amet feugiat massa dictum. Sed consequat pulvinar purus vel luctus. Aenean congue orci quis justo hendrerit, id rhoncus quam egestas. Aliquam erat volutpat. Duis est orci, maximus tincidunt orci vel, vestibulum finibus velit. Cras ante lorem, rhoncus quis nisi quis, efficitur placerat turpis. Proin lacus nisi, pharetra ac nulla quis, hendrerit aliquet orci. Vivamus convallis erat non nisi dapibus cursus.    ",
        "5 - Aliquam pharetra tempor nibh vitae blandit. Suspendisse vel ligula rutrum, rhoncus nisl eu, pellentesque diam. Nunc placerat ac libero ut mollis. Nunc eu orci egestas, blandit ipsum ac, accumsan odio. Ut at condimentum urna. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Nunc luctus lacus et semper laoreet. In hac habitasse platea dictumst. Mauris fringilla gravida eros pulvinar accumsan. Curabitur cursus bibendum mi. Nulla ipsum massa, vehicula nec condimentum in, consequat sed nibh. Curabitur tempor scelerisque ornare. Morbi dapibus ex in ex convallis egestas. Donec vehicula erat id ex tempor, id rutrum tellus pretium. Vestibulum maximus eget lacus ac sodales. Sed ac felis sed dui ullamcorper lacinia.     ",
        "6 - Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer at laoreet dolor, vitae pretium est. Donec iaculis elit felis, nec mollis erat pulvinar vel. Ut dignissim ex sed ante scelerisque, at blandit massa facilisis. Duis accumsan non nisi ac accumsan. Aenean in faucibus augue, nec imperdiet quam. Nullam non justo mi. Donec eleifend venenatis ante, eget euismod sapien tempus eu. Vestibulum nulla ipsum, volutpat et orci ac, consectetur cursus tortor. Suspendisse tristique lectus vel neque interdum pulvinar at eu nibh. Phasellus sed nulla augue.   ",
        "7 - Nam sollicitudin arcu augue, vel pulvinar felis tincidunt at. Ut tempor id lorem ac imperdiet. Proin ut eros dapibus, rhoncus leo eget, vehicula lacus. Sed et ex et turpis hendrerit dictum. Phasellus dictum nibh vitae viverra tristique. Aenean dapibus dictum velit, ac efficitur tortor consectetur sit amet. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Etiam sapien nisi, iaculis at posuere eu, imperdiet vitae sem. Ut pharetra turpis augue, eu maximus nunc congue ut. Curabitur in congue turpis. Praesent vel lobortis elit. Sed ac sodales nisi. In hac habitasse platea dictumst.   ",
        "8 - Nulla hendrerit lectus mi. Aliquam erat volutpat. Fusce tristique dolor eget tellus blandit varius. Proin et nunc pharetra, elementum tortor nec, imperdiet felis. Proin vitae arcu erat. Sed maximus quis quam vitae tristique. Ut tempus velit justo, id posuere nulla luctus id. Vestibulum quis urna id dolor eleifend gravida in at elit.   ",
        "9 - Interdum et malesuada fames ac ante ipsum primis in faucibus. Nulla cursus eros eget elit tempus, in cursus tortor tempus. Curabitur quis volutpat mauris. Vivamus posuere orci id lectus condimentum, sit amet feugiat massa dictum. Sed consequat pulvinar purus vel luctus. Aenean congue orci quis justo hendrerit, id rhoncus quam egestas. Aliquam erat volutpat. Duis est orci, maximus tincidunt orci vel, vestibulum finibus velit. Cras ante lorem, rhoncus quis nisi quis, efficitur placerat turpis. Proin lacus nisi, pharetra ac nulla quis, hendrerit aliquet orci. Vivamus convallis erat non nisi dapibus cursus.   ",
        "10 -Aliquam pharetra tempor nibh vitae blandit. Suspendisse vel ligula rutrum, rhoncus nisl eu, pellentesque diam. Nunc placerat ac libero ut mollis. Nunc eu orci egestas, blandit ipsum ac, accumsan odio. Ut at condimentum urna. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Nunc luctus lacus et semper laoreet. In hac habitasse platea dictumst. Mauris fringilla gravida eros pulvinar accumsan. Curabitur cursus bibendum mi. Nulla ipsum massa, vehicula nec condimentum in, consequat sed nibh. Curabitur tempor scelerisque ornare. Morbi dapibus ex in ex convallis egestas. Donec vehicula erat id ex tempor, id rutrum tellus pretium. Vestibulum maximus eget lacus ac sodales. Sed ac felis sed dui ullamcorper lacinia.    ",
        "11 - Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer at laoreet dolor, vitae pretium est. Donec iaculis elit felis, nec mollis erat pulvinar vel. Ut dignissim ex sed ante scelerisque, at blandit massa facilisis. Duis accumsan non nisi ac accumsan. Aenean in faucibus augue, nec imperdiet quam. Nullam non justo mi. Donec eleifend venenatis ante, eget euismod sapien tempus eu. Vestibulum nulla ipsum, volutpat et orci ac, consectetur cursus tortor. Suspendisse tristique lectus vel neque interdum pulvinar at eu nibh. Phasellus sed nulla augue.  ",
        "12 - Nam sollicitudin arcu augue, vel pulvinar felis tincidunt at. Ut tempor id lorem ac imperdiet. Proin ut eros dapibus, rhoncus leo eget, vehicula lacus. Sed et ex et turpis hendrerit dictum. Phasellus dictum nibh vitae viverra tristique. Aenean dapibus dictum velit, ac efficitur tortor consectetur sit amet. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Etiam sapien nisi, iaculis at posuere eu, imperdiet vitae sem. Ut pharetra turpis augue, eu maximus nunc congue ut. Curabitur in congue turpis. Praesent vel lobortis elit. Sed ac sodales nisi. In hac habitasse platea dictumst.  ",
        "13 - Nulla hendrerit lectus mi. Aliquam erat volutpat. Fusce tristique dolor eget tellus blandit varius. Proin et nunc pharetra, elementum tortor nec, imperdiet felis. Proin vitae arcu erat. Sed maximus quis quam vitae tristique. Ut tempus velit justo, id posuere nulla luctus id. Vestibulum quis urna id dolor eleifend gravida in at elit.  ",
        "14 - Interdum et malesuada fames ac ante ipsum primis in faucibus. Nulla cursus eros eget elit tempus, in cursus tortor tempus. Curabitur quis volutpat mauris. Vivamus posuere orci id lectus condimentum, sit amet feugiat massa dictum. Sed consequat pulvinar purus vel luctus. Aenean congue orci quis justo hendrerit, id rhoncus quam egestas. Aliquam erat volutpat. Duis est orci, maximus tincidunt orci vel, vestibulum finibus velit. Cras ante lorem, rhoncus quis nisi quis, efficitur placerat turpis. Proin lacus nisi, pharetra ac nulla quis, hendrerit aliquet orci. Vivamus convallis erat non nisi dapibus cursus.  ",
        "15 - Aliquam pharetra tempor nibh vitae blandit. Suspendisse vel ligula rutrum, rhoncus nisl eu, pellentesque diam. Nunc placerat ac libero ut mollis. Nunc eu orci egestas, blandit ipsum ac, accumsan odio. Ut at condimentum urna. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Nunc luctus lacus et semper laoreet. In hac habitasse platea dictumst. Mauris fringilla gravida eros pulvinar accumsan. Curabitur cursus bibendum mi. Nulla ipsum massa, vehicula nec condimentum in, consequat sed nibh. Curabitur tempor scelerisque ornare. Morbi dapibus ex in ex convallis egestas. Donec vehicula erat id ex tempor, id rutrum tellus pretium. Vestibulum maximus eget lacus ac sodales. Sed ac felis sed dui ullamcorper lacinia.   ",
        "16 - Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer at laoreet dolor, vitae pretium est. Donec iaculis elit felis, nec mollis erat pulvinar vel. Ut dignissim ex sed ante scelerisque, at blandit massa facilisis. Duis accumsan non nisi ac accumsan. Aenean in faucibus augue, nec imperdiet quam. Nullam non justo mi. Donec eleifend venenatis ante, eget euismod sapien tempus eu. Vestibulum nulla ipsum, volutpat et orci ac, consectetur cursus tortor. Suspendisse tristique lectus vel neque interdum pulvinar at eu nibh. Phasellus sed nulla augue.  ",
        "17 - Nam sollicitudin arcu augue, vel pulvinar felis tincidunt at. Ut tempor id lorem ac imperdiet. Proin ut eros dapibus, rhoncus leo eget, vehicula lacus. Sed et ex et turpis hendrerit dictum. Phasellus dictum nibh vitae viverra tristique. Aenean dapibus dictum velit, ac efficitur tortor consectetur sit amet. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Etiam sapien nisi, iaculis at posuere eu, imperdiet vitae sem. Ut pharetra turpis augue, eu maximus nunc congue ut. Curabitur in congue turpis. Praesent vel lobortis elit. Sed ac sodales nisi. In hac habitasse platea dictumst.  ",
        "18 - Nulla hendrerit lectus mi. Aliquam erat volutpat. Fusce tristique dolor eget tellus blandit varius. Proin et nunc pharetra, elementum tortor nec, imperdiet felis. Proin vitae arcu erat. Sed maximus quis quam vitae tristique. Ut tempus velit justo, id posuere nulla luctus id. Vestibulum quis urna id dolor eleifend gravida in at elit.  ",
        "19 - Interdum et malesuada fames ac ante ipsum primis in faucibus. Nulla cursus eros eget elit tempus, in cursus tortor tempus. Curabitur quis volutpat mauris. Vivamus posuere orci id lectus condimentum, sit amet feugiat massa dictum. Sed consequat pulvinar purus vel luctus. Aenean congue orci quis justo hendrerit, id rhoncus quam egestas. Aliquam erat volutpat. Duis est orci, maximus tincidunt orci vel, vestibulum finibus velit. Cras ante lorem, rhoncus quis nisi quis, efficitur placerat turpis. Proin lacus nisi, pharetra ac nulla quis, hendrerit aliquet orci. Vivamus convallis erat non nisi dapibus cursus.  ",
        "20 - Aliquam pharetra tempor nibh vitae blandit. Suspendisse vel ligula rutrum, rhoncus nisl eu, pellentesque diam. Nunc placerat ac libero ut mollis. Nunc eu orci egestas, blandit ipsum ac, accumsan odio. Ut at condimentum urna. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Nunc luctus lacus et semper laoreet. In hac habitasse platea dictumst. Mauris fringilla gravida eros pulvinar accumsan. Curabitur cursus bibendum mi. Nulla ipsum massa, vehicula nec condimentum in, consequat sed nibh. Curabitur tempor scelerisque ornare. Morbi dapibus ex in ex convallis egestas. Donec vehicula erat id ex tempor, id rutrum tellus pretium. Vestibulum maximus eget lacus ac sodales. Sed ac felis sed dui ullamcorper lacinia.    "
      ]
    };
  },
  computed: {
    photos() {
      return photos.map(photo => {
        return {
          id: photo.id,
          created_at: photo.created_at,
          thumb: photo.urls.thumb,
          small: photo.urls.small,
          regular: photo.urls.regular,
          description: photo.description,
          download: `${
            photo.links.download_location
          }/?client_id=f96ed367d8127eb886407fb3b4707af08ad1f7057c93c0a8a0ac00f4b064d86c`
        };
      });
    }
  }
};
</script>

<style>
  .test {
    columns: 200px 3;
    break-inside: avoid;
    page-break-inside: avoid;
  }
</style>


