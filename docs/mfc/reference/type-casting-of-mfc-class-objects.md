---
title: Conversión de tipos de objetos de clase de MFC
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
ms.openlocfilehash: 953acc32c3510b31c265f2d64d0a013f6dee06cc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372886"
---
# <a name="type-casting-of-mfc-class-objects"></a>Conversión de tipos de objetos de clase de MFC

Las macros de conversión de tipos proporcionan una manera de convertir un puntero determinado a un puntero que apunta a un objeto de clase específica, con o sin comprobar que la conversión es legal.

En la tabla siguiente se enumeran las macros de conversión de tipos MFC.

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Macros que convierten punteros a objetos de clase MFC

|||
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|Convierte un puntero a un puntero a un objeto de clase mientras comprueba si la conversión es legal.|
|[STATIC_DOWNCAST](#static_downcast)|Convierte un puntero a un objeto de una clase a un puntero de un tipo relacionado. En una compilación de depuración, provoca un ASSERT si el objeto no es un "tipo de" el tipo de destino.|

## <a name="dynamic_downcast"></a><a name="dynamic_downcast"></a>DYNAMIC_DOWNCAST

Proporciona una forma práctica de convertir un puntero a un puntero a un objeto de clase mientras comprueba si la conversión es legal.

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>Parámetros

*clase*<br/>
Nombre de una clase.

*puntero*<br/>
Puntero que se va a convertir a un puntero a un objeto de *clase*de tipo .

### <a name="remarks"></a>Observaciones

La macro convertirá el parámetro *de puntero* a un puntero a un objeto del tipo del parámetro de *clase.*

Si el objeto al que hace referencia el puntero es un "tipo de" la clase identificada, la macro devuelve el puntero adecuado. Si no es una conversión legal, la macro devuelve NULL.

## <a name="static_downcast"></a><a name="static_downcast"></a>STATIC_DOWNCAST

Convierte *pobject* en un puntero a un *objeto class_name.*

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase a la que se está lanzando.

*pobject*<br/>
El puntero que se va a convertir a un puntero a un *objeto class_name.*

### <a name="remarks"></a>Observaciones

*pobject* debe ser NULL o apuntar a un objeto de una clase que se deriva directa o indirectamente de *class_name*. En compilaciones de la aplicación con el símbolo de preprocesador _DEBUG definido, la macro ASSERT si *pobject* no es NULL, o si apunta a un objeto que no es un "tipo de" la clase especificada en el parámetro *class_name* (consulte [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)). En compilaciones no **_DEBUG,** la macro realiza la conversión sin ninguna comprobación de tipo.

La clase especificada *class_name* en el parámetro class_name `CObject` debe derivarse y debe utilizar la DECLARE_DYNAMIC y IMPLEMENT_DYNAMIC, la DECLARE_DYNCREATE y IMPLEMENT_DYNCREATE, o las macros DECLARE_SERIAL y IMPLEMENT_SERIAL como se explica en el artículo [CObject Class: Deriving a Class from CObject](../../mfc/deriving-a-class-from-cobject.md).

Por ejemplo, puede convertir `CMyDoc`un `pMyDoc`puntero a , `CDocument` llamado , a un puntero para usar esta expresión:

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

Si `pMyDoc` no apunta a un objeto derivado `CDocument`directa o indirectamente de , la macro ASSERT.

## <a name="see-also"></a>Consulte también

[Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)
