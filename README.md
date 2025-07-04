# OC Nuxt

- [OCTable](/_doc/datatable)
- [OCForm](/_doc/form)
- [OCFormGroup](/_doc/formgroup)
- [OCInput](/_doc/input)
- [OCCheckbox](/_doc/checkbox)
- [OCCheckboxGroup](/_doc/checkboxgroup)
- [OCRadio](/_doc/radio)
- [OCRadioGroup](/_doc/radiogroup)
- [OCTextarea](/_doc/textarea)
- [Buttons](/_doc/button)
- [Avatas](/_doc/avata)
- [OCSelect](/_doc/select)
- [OCDrawer](/_doc/drawer)
- [OCModal](/_doc/modal)
- [OCTab](/_doc/tab)
- [<a href="https://zod.dev/?id=required" target="_blank">Zod Validate</a>] ⇲
- [<a href="https://flowbite-vue.com/components/accordion" target="_blank">Flowbite</a>] ⇲

# Naming Structure

- **Page name**: `home_page`, `user_profile_page`
- **Components name**: `HeaderComponent`, `UserCardComponent`
- **Composables name**: `useAuth`, `useFetchData`
- **Util name**: `formatDate`, `parseJson`
- **Store name**: `userStore`, `cartStore`
- **Folder name**: `pages`, `components`, `productDetail` *<span style="color:orange">*not include page</span>*
- **Other**: `configSettings`, `apiClient`
- **Naming Variable**: `variableName`

# Structure

- components
  - MainModule
    - SubModule
- composables
  - mainComposable
    - subComposable
- pages
  - main_page
    - sub_page
- stores
  - mainStore
    - subStore

# Using helper

```js
const { str, apis, config } = helper();
```

## Using cookie

```js
const cookie = useCookie();

// set value
cookie.value = newData;
// get value
cookie.value;
```

## Using with api

- **url**: is a path of api or full path **/api/get** or **https://domain.com/api/get**
- **option**
  - **method**: 'post' or 'get'
  - **data**: object
  - **isGloble**: default **false**

```js
const { str, apis, config } = helper();
const { data, error } = useHttp(apis.get, {
  method: "post",
  data: {},
});
```
