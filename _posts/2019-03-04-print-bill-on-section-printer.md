---
title: Добавлена возможность выбора принтера при печати пречека  
layout: default
---
В метод [`PrintBillCheque`](http://iiko.github.io/front.api.sdk/v6/html/M_Resto_Front_Api_IOperationService_PrintBillCheque.htm) добавлен необязательный параметр `printerSelectionMode`, влияющий на выбор принтера. Это позволит плагину выбирать, печатать ли пречек на принтере отделения, где расположен заказ, или на принтере локального терминала.

Когда заведение имеет несколько отделений ([`IRestaurantSection`](http://iiko.github.io/front.api.sdk/v6/html/T_Resto_Front_Api_Data_Organization_Sections_IRestaurantSection.htm)), удобно в каждом из них установить отдельный принтер пречеков и для каждого отделения настроить печать пречеков на свой принтер, чтобы не ходить к принтеру в другом зале или на другом этаже.
При этом могут быть исключения, когда для некоторых терминалов настраивается печатать пречека на локальный принтер независимо от расположения заказа.
Обычно так настраивают главную кассу.
Прежде плагин, установленный на таком терминале, мог напечатать пречек только на привязанном к терминалу локальном принтере, что было неуместно, если плагин, будучи установленным на одном терминале, работал с заказами разных отделений.
Теперь плагин, в зависимости от сценария, может указать, печатать ли пречек на локальный принтер терминала или на принтер отделения, на столе которого расположен заказ.

Доступны следующие варианты [PrinterSelectionMode](http://iiko.github.io/front.api.sdk/v6/html/T_Resto_Front_Api_Data_Print_PrinterSelectionMode.htm):

- `BySection` — новый режим, использует принтер отделения,
- `ByTerminal` — соответствует прежнему поведению, будет использован локальный принтер терминала, а если он не задан, то будет использован принтер отделения,
- `Default` — вариант по умолчанию, в текущей реализации совпадает с вариантом `ByTerminal`.
