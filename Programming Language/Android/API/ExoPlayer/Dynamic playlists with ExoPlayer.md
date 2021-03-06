# Dynamic playlists with Exo Player
- Reference
    - From: medium
    - Writer: Toni Heidenreich
    - Date: 2018/06/29
- `DynamicConcatenatingMediaSource` to `ConcatenatingMediaSource`
- ExoPlayer 2.8.0부터 동적 플레이리스트를 다룰 수 있는 `ConcatenatingMediaSource`를 업데이트하였습니다. 새로운 media source는 매우 간단하고 직관적인 인터페이스를 갖고 있습니다.
    - `addMediaSource(mediaSource)`
    - `addMediaSource(Collection<MediaSource)`
    - `addMediaSource(index, mediaSource)`
    - `addMediaSource(index, Collection<MediaSource)`
        - 플레이리스트의 마지막/ 특정한 위치에 새로운 소스(들)를 추가함
    - `removeMediaSource(index)`
        - 특정 위치의 소스를 제거함
    - `moveMediaSource(fromIndex, toIndex)`
        - 이미 존재하는 소스를 플레이리스트에 추가함, 이것은 새로운 미디어소스 객체를 선언하지 않는점에서 유리함
    - `getMediaSource(index)`
        - 주어진 인덱스의 소스로 접근할 수 있음
    - `getSize()`
        - 현재 플레이리스트의 길이를 반환함
- 당신은 재생이 시작되기 전과 후 언제든 위의 method를 통해 thread-safe하게 아이템에 접근할 수 있을뿐만 아니라 다음 플레이리스트 아이템을 미리 버퍼링하는 gapless 재생을 보장합니다. 그리고 항상 새로운 재생 소스로의 변화를 `eventListener.onPositionDisdontinuity`를 통해 확인할 수 있습니다.
-
