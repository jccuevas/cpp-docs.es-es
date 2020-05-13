---
title: Control de eventos
ms.date: 05/07/2019
helpviewer_keywords:
- event handling [C++]
ms.assetid: 82de3f9a-2d88-470c-9527-8a5b54c8ced4
ms.openlocfilehash: cf16ea0e6e14981f1105456a5f17d68c05a9c3fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189213"
---
# <a name="event-handling"></a>Control de eventos

El control de eventos se admite principalmente para lasC++ clases com (clases que implementan objetos com, normalmente mediante clases ATL o el atributo [CoClass](../windows/coclass.md) ). Para obtener más información, vea [control de eventos en com](../cpp/event-handling-in-com.md).

El control de eventos también se admite para las clases de C++ nativo (clases de C++ que no implementan objetos COM); sin embargo, esa compatibilidad está desusada y se quitará en futuras versiones.  Para obtener más información, vea [control de eventos C++en nativo ](../cpp/event-handling-in-native-cpp.md).

El control de eventos admite el uso de único subproceso y multiproceso y protege los datos de acceso multiproceso simultáneo. También permite que se deriven subclases de clases del origen de eventos o del receptor y que se admita el suministro y la recepción de eventos extendidos en la clase derivada.

El compilador de Microsoft C++ incluye atributos y palabras clave para declarar eventos y controladores de eventos. Los atributos y las palabras clave de eventos se pueden utilizar en programas de CLR y en programas de C++ nativo.

|Tema|Descripción|
|-----------|-----------------|
|[event_source](../windows/attributes/event-source.md)|Crea un origen de eventos.|
|[event_receiver](../windows/attributes/event-receiver.md)|Crea un receptor de eventos (receptor).|
|[__event](../cpp/event.md)|Declara un evento.|
|[__raise](../cpp/raise.md)|Resalta el sitio de llamada de un evento.|
|[__hook](../cpp/hook.md)|Asocia un método de control a un evento.|
|[__unhook](../cpp/unhook.md)|Disocia un método de control de un evento.|

## <a name="see-also"></a>Consulte también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
