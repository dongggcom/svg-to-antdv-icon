# svg-to-antdv-icon

transform svg to antd icon

## Basic Usage

copy `*.svg` in `svg/` and run `yarn g`, it will create ts files in `src`, which transform svg file in `src/asn`.

### Transform svg files
create svg directory
`mkdir svg`

move or copy svg files to svg directory
`cp icon.svg svg/`

run command
`yarn g`

find transformed file in `src/asn` like `Icon.ts`

### How to use in your project

create a component directory like `components/icon`, copy transformed file to this directory, like `components/icon/asn/Icon.ts`.

create a `index.ts` in `component/icon`.
```ts
import {AntdIconProps} from '@ant-design/icons-vue/lib/components/AntdIcon';
import AntdIcon from '@ant-design/icons-vue/es/components/AntdIcon';
import {FunctionalComponent} from 'vue';
import IconSvg from './asn/Icon';


export const MyIcon: FunctionalComponent<AntdIconProps> = (props, context) => {
    const p = {...props, ...context.attrs};
    return <AntdIcon {...p} icon={IconSvg}></AntdIcon>;
};
```

you will used in you `*.vue` like
```vue
<my-icon />
```

## F&Q

### my icon has not change color in hover

you need to replace `currentColor` from svg attribute like `stroke`.

```json
{"stroke":"currentColor"}
```

### transformed icon has filled with black

there are some reason, which your svg file painting with fill, that would find attribute `fill: none`. the same way of that, you need to append this attribute in transform ts file. 