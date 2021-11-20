<template>
  <div>
    <v-card>
      <v-card-title>
        <v-text-field
          v-model="search"
          placeholder="Search Post"
          append-icon="mdi-magnify"
          label="Search"
          single-line
          hide-details
        ></v-text-field>
      </v-card-title>
      <v-data-table
        :headers="headers"
        :items="desserts"
        multi-sort
        :items-per-page="5"
        :search="search"
        class="elevation-1"
      >
        <template v-slot:item.thumbnail="{ item }">
          <img
            src="@/assets/img/yapim.png"
            width="160"
            height="160"
            class="rounded"
          />
        </template>
        <template v-slot:item.actions="{ item }">
          <v-icon @click.stop="editDialog = true">
            mdi-pencil
          </v-icon>
          <v-icon @click.stop="deleteDialog = true">
            mdi-delete
          </v-icon>
        </template>
      </v-data-table>
    </v-card>

    <!-- Edit Dialog -->
    <v-dialog
      v-model="editDialog"
      fullscreen
      hide-overlay
      transition="dialog-bottom-transition"
    >
      <v-card>
        <v-toolbar dark color="primary" elevation="0">
          <v-btn icon dark @click="editDialog = false">
            <v-icon>mdi-close</v-icon>
          </v-btn>
          <v-toolbar-title>Edit Post</v-toolbar-title>
          <!-- <v-spacer></v-spacer> -->
        </v-toolbar>

        <v-card-text>
          <v-container>
            <v-row>
              <v-col cols="12" sm="6" md="4">
                <v-text-field label="Legal first name*" required></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="4">
                <v-text-field
                  label="Legal middle name"
                  hint="example of helper text only on focus"
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="4">
                <v-text-field
                  label="Legal last name*"
                  hint="example of persistent helper text"
                  persistent-hint
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12">
                <v-text-field label="Email*" required></v-text-field>
              </v-col>
              <v-col cols="12">
                <v-text-field
                  label="Password*"
                  type="password"
                  required
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="6">
                <v-select
                  :items="['0-17', '18-29', '30-54', '54+']"
                  label="Age*"
                  required
                ></v-select>
              </v-col>
              <v-col cols="12" sm="6">
                <v-autocomplete
                  :items="[
                    'Skiing',
                    'Ice hockey',
                    'Soccer',
                    'Basketball',
                    'Hockey',
                    'Reading',
                    'Writing',
                    'Coding',
                    'Basejump',
                  ]"
                  label="Interests"
                  multiple
                ></v-autocomplete>
              </v-col>
            </v-row>
          </v-container>
          <small>*indicates required field</small>
        </v-card-text>
        <!-- Actions -->
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="blue darken-1" text @click="editDialog = false">
            Close
          </v-btn>
          <v-btn color="blue darken-1" text @click="editDialog = false">
            Save
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <!-- Delete Dialog -->
    <v-dialog v-model="deleteDialog" max-width="400">
      <v-card>
        <v-card-title class="text-h6">
          Are you sure delete this post ?
        </v-card-title>

        <v-card-text>
          Your action can't be undone!
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>

          <v-btn color="gray darken-1" text @click="deleteDialog = false">
            Cancel
          </v-btn>
          <v-btn color="red darken-1" text @click="deleteDialog = false">
            Delete
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
  data() {
    return {
      deleteDialog: false,
      editDialog: false,
      search: '',
      headers: [
        { text: 'Title', value: 'title' },
        { text: 'Thumbnail', value: 'thumbnail' },
        { text: 'Username Uploader', value: 'user' },
        { text: 'Text', value: 'text' },
        { text: 'Actions', value: 'actions' },
      ],
      desserts: [
        {
          title: 'Frozen Yogurt',
          thumbnail: '../../../assets/img/yapim.png',
          user: 'ridoananda',
          text:
            'Lorem ipsum dolor sit amet consectetur adipisicing elit. Aspernatur assumenda porro repudiandae fugit eveniet possimus velit odio nesciunt ipsa, sapiente asperiores in, ipsam molestiae? Id, labore. Delectus minus sit veniam corrupti odit quos excepturi vero quas voluptatum commodi, quidem soluta et in rerum velit tempore accusantium maiores dolor dolorem temporibus asperiores reiciendis quia tempora illo! Consequatur vero minus aut architecto aperiam aspernatur at sunt. Eligendi pariatur eius eaque? Iste ab autem repellat vel iure sequi blanditiis aut, velit nobis pariatur officia, voluptatum molestiae eos laborum nam ut ex! Tempore praesentium at consequatur obcaecati molestiae odit non eaque alias quod numquam.',
          protein: 4.0,
          iron: '1%',
        },
        {
          title: 'Ice cream sandwich',
          thumbnail: '../../../assets/img/yapim.png',
          user: 'ridoananda',
          text:
            'Lorem ipsum dolor sit amet consectetur adipisicing elit. Aspernatur assumenda porro repudiandae fugit eveniet possimus velit odio nesciunt ipsa, sapiente asperiores in, ipsam molestiae? Id, labore. Delectus minus sit veniam corrupti odit quos excepturi vero quas voluptatum commodi, quidem soluta et in rerum velit tempore accusantium maiores dolor dolorem temporibus asperiores reiciendis quia tempora illo! Consequatur vero minus aut architecto aperiam aspernatur at sunt. Eligendi pariatur eius eaque? Iste ab autem repellat vel iure sequi blanditiis aut, velit nobis pariatur officia, voluptatum molestiae eos laborum nam ut ex! Tempore praesentium at consequatur obcaecati molestiae odit non eaque alias quod numquam.',
          protein: 4.3,
          iron: '1%',
        },
        {
          title: 'Eclair',
          thumbnail: '../../../assets/img/yapim.png',
          user: 'ridoananda',
          text:
            'Lorem ipsum dolor sit amet consectetur adipisicing elit. Aspernatur assumenda porro repudiandae fugit eveniet possimus velit odio nesciunt ipsa, sapiente asperiores in, ipsam molestiae? Id, labore. Delectus minus sit veniam corrupti odit quos excepturi vero quas voluptatum commodi, quidem soluta et in rerum velit tempore accusantium maiores dolor dolorem temporibus asperiores reiciendis quia tempora illo! Consequatur vero minus aut architecto aperiam aspernatur at sunt. Eligendi pariatur eius eaque? Iste ab autem repellat vel iure sequi blanditiis aut, velit nobis pariatur officia, voluptatum molestiae eos laborum nam ut ex! Tempore praesentium at consequatur obcaecati molestiae odit non eaque alias quod numquam.',
          protein: 6.0,
          iron: '7%',
        },
        {
          title: 'Cupcake',
          thumbnail: '../../../assets/img/yapim.png',
          user: 'ridoananda',
          text:
            'Lorem ipsum dolor sit amet consectetur adipisicing elit. Aspernatur assumenda porro repudiandae fugit eveniet possimus velit odio nesciunt ipsa, sapiente asperiores in, ipsam molestiae? Id, labore. Delectus minus sit veniam corrupti odit quos excepturi vero quas voluptatum commodi, quidem soluta et in rerum velit tempore accusantium maiores dolor dolorem temporibus asperiores reiciendis quia tempora illo! Consequatur vero minus aut architecto aperiam aspernatur at sunt. Eligendi pariatur eius eaque? Iste ab autem repellat vel iure sequi blanditiis aut, velit nobis pariatur officia, voluptatum molestiae eos laborum nam ut ex! Tempore praesentium at consequatur obcaecati molestiae odit non eaque alias quod numquam.',
          protein: 4.3,
          iron: '8%',
        },
        {
          title: 'Gingerbread',
          thumbnail: '../../../assets/img/yapim.png',
          user: 'ridoananda',
          text:
            'Lorem ipsum dolor sit amet consectetur adipisicing elit. Aspernatur assumenda porro repudiandae fugit eveniet possimus velit odio nesciunt ipsa, sapiente asperiores in, ipsam molestiae? Id, labore. Delectus minus sit veniam corrupti odit quos excepturi vero quas voluptatum commodi, quidem soluta et in rerum velit tempore accusantium maiores dolor dolorem temporibus asperiores reiciendis quia tempora illo! Consequatur vero minus aut architecto aperiam aspernatur at sunt. Eligendi pariatur eius eaque? Iste ab autem repellat vel iure sequi blanditiis aut, velit nobis pariatur officia, voluptatum molestiae eos laborum nam ut ex! Tempore praesentium at consequatur obcaecati molestiae odit non eaque alias quod numquam.',
          protein: 3.9,
          iron: '16%',
        },
        {
          title: 'Jelly bean',
          thumbnail: '../../../assets/img/yapim.png',
          user: 'ridoananda',
          text:
            'Lorem ipsum dolor sit amet consectetur adipisicing elit. Aspernatur assumenda porro repudiandae fugit eveniet possimus velit odio nesciunt ipsa, sapiente asperiores in, ipsam molestiae? Id, labore. Delectus minus sit veniam corrupti odit quos excepturi vero quas voluptatum commodi, quidem soluta et in rerum velit tempore accusantium maiores dolor dolorem temporibus asperiores reiciendis quia tempora illo! Consequatur vero minus aut architecto aperiam aspernatur at sunt. Eligendi pariatur eius eaque? Iste ab autem repellat vel iure sequi blanditiis aut, velit nobis pariatur officia, voluptatum molestiae eos laborum nam ut ex! Tempore praesentium at consequatur obcaecati molestiae odit non eaque alias quod numquam.',
          protein: 0.0,
          iron: '0%',
        },
        {
          title: 'Lollipop',
          thumbnail: '../../../assets/img/yapim.png',
          user: 'ridoananda',
          text:
            'Lorem ipsum dolor sit amet consectetur adipisicing elit. Aspernatur assumenda porro repudiandae fugit eveniet possimus velit odio nesciunt ipsa, sapiente asperiores in, ipsam molestiae? Id, labore. Delectus minus sit veniam corrupti odit quos excepturi vero quas voluptatum commodi, quidem soluta et in rerum velit tempore accusantium maiores dolor dolorem temporibus asperiores reiciendis quia tempora illo! Consequatur vero minus aut architecto aperiam aspernatur at sunt. Eligendi pariatur eius eaque? Iste ab autem repellat vel iure sequi blanditiis aut, velit nobis pariatur officia, voluptatum molestiae eos laborum nam ut ex! Tempore praesentium at consequatur obcaecati molestiae odit non eaque alias quod numquam.',
          protein: 0,
          iron: '2%',
        },
        {
          title: 'Honeycomb',
          thumbnail: '../../../assets/img/yapim.png',
          user: 'ridoananda',
          text:
            'Lorem ipsum dolor sit amet consectetur adipisicing elit. Aspernatur assumenda porro repudiandae fugit eveniet possimus velit odio nesciunt ipsa, sapiente asperiores in, ipsam molestiae? Id, labore. Delectus minus sit veniam corrupti odit quos excepturi vero quas voluptatum commodi, quidem soluta et in rerum velit tempore accusantium maiores dolor dolorem temporibus asperiores reiciendis quia tempora illo! Consequatur vero minus aut architecto aperiam aspernatur at sunt. Eligendi pariatur eius eaque? Iste ab autem repellat vel iure sequi blanditiis aut, velit nobis pariatur officia, voluptatum molestiae eos laborum nam ut ex! Tempore praesentium at consequatur obcaecati molestiae odit non eaque alias quod numquam.',
          protein: 6.5,
          iron: '45%',
        },
        {
          title: 'Donut',
          thumbnail: '../../../assets/img/yapim.png',
          user: 'ridoananda',
          text:
            'Lorem ipsum dolor sit amet consectetur adipisicing elit. Aspernatur assumenda porro repudiandae fugit eveniet possimus velit odio nesciunt ipsa, sapiente asperiores in, ipsam molestiae? Id, labore. Delectus minus sit veniam corrupti odit quos excepturi vero quas voluptatum commodi, quidem soluta et in rerum velit tempore accusantium maiores dolor dolorem temporibus asperiores reiciendis quia tempora illo! Consequatur vero minus aut architecto aperiam aspernatur at sunt. Eligendi pariatur eius eaque? Iste ab autem repellat vel iure sequi blanditiis aut, velit nobis pariatur officia, voluptatum molestiae eos laborum nam ut ex! Tempore praesentium at consequatur obcaecati molestiae odit non eaque alias quod numquam.',
          protein: 4.9,
          iron: '22%',
        },
        {
          title: 'KitKat',
          thumbnail: '../../../assets/img/yapim.png',
          user: 'ridoananda',
          text:
            'Lorem ipsum dolor sit amet consectetur adipisicing elit. Aspernatur assumenda porro repudiandae fugit eveniet possimus velit odio nesciunt ipsa, sapiente asperiores in, ipsam molestiae? Id, labore. Delectus minus sit veniam corrupti odit quos excepturi vero quas voluptatum commodi, quidem soluta et in rerum velit tempore accusantium maiores dolor dolorem temporibus asperiores reiciendis quia tempora illo! Consequatur vero minus aut architecto aperiam aspernatur at sunt. Eligendi pariatur eius eaque? Iste ab autem repellat vel iure sequi blanditiis aut, velit nobis pariatur officia, voluptatum molestiae eos laborum nam ut ex! Tempore praesentium at consequatur obcaecati molestiae odit non eaque alias quod numquam.',
          protein: 7,
          iron: '6%',
        },
      ],
    }
  },
}
</script>

<style></style>
