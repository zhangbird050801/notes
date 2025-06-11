![[a1c3ea6ff2de8c4afc45f0272eedb7c.png]]

![[8a70fa07a1421d68a91f654e7412f21.png]]

```vue
<scroll-view class="notice-list" scroll-x="true" show-scrollbar="false">
	<view v-for="(notice, index) in noticeList" :key="index" class="notice-item">
	  <text class="notice-title">{{ notice.title }}</text>
	  <text class="notice-time">{{ notice.time }}</text>
	</view>
</scroll-view>

.notice-list { display: flex; flex-direction: row; overflow-x: scroll;
white-space: nowrap; } .notice-item { display: inline-block; width: 300rpx;
margin-right: 20rpx; padding: 20rpx; background-color: #f8f8f8; border-radius:
8rpx; box-shadow: 0 2rpx 8rpx rgba(0, 0, 0, 0.1); }
```

```
<SectionCard>
      <swiper :indicator-dots="true" :autoplay="true" :interval="5000" :duration="1000">
        <SwiperItem v-for="(item, index) in items" :key="index">
          <view class="swiper-item">
            <text>{{ item }}:{{ index }}</text>
          </view>
        </SwiperItem>
      </swiper>
    </SectionCard>

const items = ref(['页面 1', '页面 2', '页面 3']);

swiper {
  height: 200px;
}

.swiper-item {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  font-size: 18px;
  color: #333;
  background-color: #dcdcdc;
}
```
