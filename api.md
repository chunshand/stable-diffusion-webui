# 说明文档

暂定接口地址：http://222.187.226.110:53379

# 接口说明

- 文生图

```js
// /sdapi/v1/txt2img Post

let data = {
    // 宽
    width:512,
    // 高
    height:512,
    // 每次生成张数
    batch_size:1,
    // 正向提示词
    prompt:"",
    // 负面提示词
    negative_prompt: `deleted, old, oldest, ((censored)), ((bad aesthetic)), (muli view),(fused fingers:1.61051), (too many fingers:1.61051), (unclear eyes:1.331), (underexposed, overexposed, low contrast, greyscale, monochrome:1.2), (out of frame, cut off, cropped), (cloning, clones, same face, multiple girls), ((3d, toon \(style\), sketch, cartoonized)), (male face, obesity, fat,giantess, giant, dwarf), (lowres, worst quality, low quality, normal quality, jpep artifacts, blurry vision, blurry, watermark, signature, bad art, beginner, amateur, draft, grainy, text, title, logo, error, toon \(style\):1.3), ((bad anatomy, bad proportions, deformed, bad perspective, forced perspective), bad hands, poorly drawn hands, mutated hand, bad feet, bad leg, poorly drawn feet, extra arms, missing limbs, missing arms,bad arm, missing fingers, extra fingers, wrong fingers, twisted fingers,blurred fingers, extra digit, fewer digits, extra limbs, extra legs, leg disfigured, poorly drawn face, distorted face, strabismus, ugly, ugly man, ugly face, scar on face, face defect, facial tattoo, crescent facial mark, facial mark, mask, veil, faceless:1.5), (nsfw, large breasts, huge breasts, looking back, nude, nake breasts, direct lighting, lens flare, colorful background, warm colors, strong color, high color saturation, colorful:1.2), badhandsv5-neg, badhandv4, EasyNegative, easynegative, ng_deepnegative_v1_75t, verybadimagenegative_v1.3, painting, sketches, (low quality, worst quality:1.5),
deformed, bad anatomy, lowres, monochrome, grayscale,ugly face, inaccurate limb, bad hands, mutated hands,mutated legs, missing fingers, extra fingers`,
    // 步长
    steps:30,

    seed:-1,
    // 是否开启高清修复
    enable_hr:false,
    // 高清修复算法
    hr_upscaler:"ESRGAN_4x",

    // 额外增加
    // 任务id 
    task_id:""

}

// 风格为追加到prompt字段后： "((best quality)), ((masterpiece))," <prompt> [<lora:loraName:(0.5权重)>]


```
返回值说明
```js
let res = {
    // 图片
    images:[],
    // 图片信息 json
    info:""，
    parameters:{}
}
```

- 进度获取 Progress

请求值
```js
// /sdapi/v1/progress Get
let data ={
    task_id:""
}

```
返回值说明

```js
let res = {
    // 预览图
    current_image:"",
    // 预计
    eta_relative:0,
    // 进度
    progress:0,

    state:{
        sampling_step:30,
        sampling_steps:30,
        task_id:""
    }
}
```

- 切换模型

```js
// /sdapi/v1/options POST

let data = {
    sd_model_checkpoint:"模型名称"
}
```

无返回 关注响应状态即可