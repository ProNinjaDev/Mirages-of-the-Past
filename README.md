# Mirages-of-the-Past

VR игра, разработанная на движке Unity. Для работы с VR использовался XR Origin.

Игровая область состоит из Terrain, на котором есть различные локации, по которым последовательно разбросаны головоломки

Создание Локации:

Локация включает в себя несколько основных элементов: составной остров, продолговатый овраг, несколько холмов с ручьем. Главный элемент ланшавта - terrain (в нашей игре их два, они отличаются мелкими временными деталями, потому что игрок может перемещаться во времени и некоторые составляющие карты будут меняться), рельев создавался полностью самостоятельно при помощи инструмента "Terrain tools", изначально terrain был поднят вверх на 50 единиц, затем при помощи инструмента "Raise or Lower Terrain" были созданы холмы и низины, прокопан каналы для реки и ручья, добавил немного шума на локацию, затем при помощи инструмента "Smooth Hight" были сглажены все неровности, так как локация представляет из себя лесной частный участок на котором не может быть резких перепадов высоты. Когда мы закончили с рельефом - приступили к текстурированнию Terrain'a при помощи инструмента "Paint Texture", на Terrain наложенны несколько текстур, такие как: трава, земля с грязью, трава с землй, окоменелости, желтая трава, гравий и еще несколько маловстречающихся на локации текстур. Когда мы закончили создавть основную часть ланшавта - стали переносить модели из Blender'a в проект, такие как: дом, сарай, мосты, костер, печь, машины, клумбы с цветами, мебель для дома и многие другие. Разобравшись с расположение элементов - засадили Terrain травой при помощи инструмента "Paint Details" (в проекте также несколько видов объемной травы, а именно: классическая-зеленая, выцветшая - желтая, и темная- немного сгоревшая для другого времени), затем в проект были добавлены и рассположены при помощи инструмента "Paint Trees" по локации, заранее созданные, деревья (они также продублированны для другого времени в игре, а именно создано 5 деревьев с зеленой листвой и 5 деревьев для осеннего времени года - с желтой). Ограничением карты является живая изгородь, которая была высажена по периметру всей карты (ее мы взяли из Scetchfab'a). Карта содержит несколько SkyBox (Солнечный и второй с тучами, пасмурный). Финальной частью визуального оформления стало добавление эффектов "Post Processing" на главную камеру (добавлено несколько эффектов: Ambiend Occlusion, Auto Exposure, Bloom, Chromatic Aberration, Color Grading, Moutine Blur)


Создание головоломок:

1. Головоломка с фонарём. В доме мы должны найти части, которые должны вставить в область перед фонарём. Тени, отброшенные вставленными частями, покажут каким образом нужно установить стрелки часов в доме, чтобы перейти к следующей головоломке.
2. Головоломка со стеллажом и бутылками. В подвале в одной из комнат можно заметить на столе две бутылки и стеллаж с бутылками. На одной из предыдущих головоломок игрок получил подсказку, каким образом нужно расположить бутылки, чтобы открылась потайная комната.
3. Головоломка с патефоном. Игрок находит пластинку, которую нужно вставить в патефон. Играющая композиция даст подсказку где искать надпись, которая является ключом к решению следующей головоломки.
4. Головоломка со шкатулкой. На нескольких предыдущих головоломках получаем зашифрованные коды, которые нужно объединить, чтобы получить 3-х значный код. Его нужно ввести на найденной шкатулке. Чтобы ввести код, нужно взять шкатулку в правую руку и стиком левого контроллера поставить цифры в нужном порядке.
5. Головоломка со льдом и котелком. После головоломки с фонарём мы можем открыть дверку часов, чтобы получить ручку для холодильника. В холодильнике берём кубик льда. Бросаем его в котелок на улице и по триггерному коллайдеру срабатывает скрипт, который включает анимацию таяния льда, достаём ключ.
6. Головоломка с гильзами. В тайной комнате в подвале мы находим винтовку. Отодвигаем затвор, вылетает гильза, на которой написан зашифрованный код. На затворе висит скрипт, связывающий настройки Rigidbody, Configurable Joint и Animator. При достижении нужного смещения активируется анимация гильзы, потом анимация затвора, возвращающая его на исходное положение. Затвор блокируется. Configurable Joint позволяет вращать затвор вокруг одной оси и передвигать его по одной оси.
7. Головоломка с телескопом. На улице стоит телескоп, через который мы можем увидеть зашифрованный код. Модель телескопа разделена на две части: верхнюю и нижнюю. На верхней части висит компонент Hinge Joint, который фиксирует её вращение в определённой плоскости. Hinge Joint связан с Rigidbody, замораживающим положение объекта во всех осях. Также на верхней части есть компонент XR Grab Interactable, позволяющий игроку взаимодействовать с телескопом с помощью контроллеров. 
