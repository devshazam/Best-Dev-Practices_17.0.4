1_ <Image ... > - это клиентский крмпонент ('use client')
    - ref: https://nextjs.org/docs/app/api-reference/components/image
    - next сомостоятельно сжимает картинку и преобразует (png, jpg) в webp
    - Картинка становится lazy_load по умолчанию
    - priority - используется для самой главной картинкки
    - placeholder="blur" - для картинки во время загрузки
    - Делать отдельные минимальные картинки в формате webp для мобильного и ПК 
    - Все иконки в формате svg
    - Размер картиинок до 50 kB
    - Минимизировать картинки на сайте!
    - sizes props - использовать для автомотической оптимизации картинки под разные устройства в ззависимости от ширины экрана
    - если возможно использовать svg
    - Верхнюю основную картинку нужно разделить на 3 более мелких картинки и подгружать priority 425 px
    - priority для изображений первого экрана для улудшения показателей LPC