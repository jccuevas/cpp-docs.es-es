---
title: Conversión de tipos de objetos de clase de MFC
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.classes
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
ms.openlocfilehash: 3107b860747bc2434ae9afca39b517d8dcc9eb01
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299366"
---
# <a name="type-casting-of-mfc-class-objects"></a>Conversión de tipos de objetos de clase de MFC

Macros de conversión de tipo proporcionan una manera de convertir un puntero especificado a un puntero que señala a un objeto de clase específica, con o sin comprobar que la conversión es legal.

En la tabla siguiente se enumera las macros de conversión de tipo MFC.

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Macros que convertir punteros a objetos de clase MFC

|||
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|Convierte un puntero a un puntero a un objeto de clase al comprobar si la conversión es válida.|
|[STATIC_DOWNCAST](#static_downcast)|Convierte un puntero a un objeto de una clase a un puntero de un tipo relacionado. En una compilación de depuración, produce una aserción si el objeto no es un "tipo de" el tipo de destino.|

##  <a name="dynamic_downcast"></a>  DYNAMIC_DOWNCAST

Proporciona una forma práctica para convertir un puntero a un puntero a un objeto de clase al comprobar si la conversión es válida.

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>Parámetros

*class*<br/>
El nombre de una clase.

*pointer*<br/>
Un puntero a convertirse en un puntero a un objeto de tipo *clase*.

### <a name="remarks"></a>Comentarios

La macro convertirá la *puntero* parámetro a un puntero a un objeto de la *clase* tipo del parámetro.

Si el objeto al que hace referencia el puntero es un "tipo de" la clase identificada, la macro devuelve el puntero adecuado. Si no es una conversión válidas, la macro devuelve NULL.

##  <a name="static_downcast"></a>  STATIC_DOWNCAST

Las conversiones *pobject* a un puntero a un *class_name* objeto.

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>Parámetros

*class_name*<br/>
El nombre de la clase que se va a convertir en.

*pobject*<br/>
El puntero para convertirse en un puntero a un *class_name* objeto.

### <a name="remarks"></a>Comentarios

*pObject* debe ser NULL o seleccione un objeto de una clase que se deriva directa o indirectamente, de *class_name*. En las compilaciones de la aplicación con el símbolo de preprocesador _DEBUG definido, la macro se producirá una aserción si *pobject* no es NULL, o si señala a un objeto que no es un "tipo de" la clase especificada en el *class_name*parámetro (consulte [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof)). En el que no sean de **_DEBUG** compilaciones, la macro realiza la conversión sin ninguna comprobación de tipo.

La clase especificada en el *class_name* parámetro debe derivarse de `CObject` y debe usar el DECLARE_DYNAMIC y IMPLEMENT_DYNAMIC, el DECLARE_DYNCREATE y IMPLEMENT_DYNCREATE, o el DECLARE_SERIAL y IMPLEMENT_ SERIE macros como se explican en el artículo [CObject (clase): Derivar una clase de CObject](../../mfc/deriving-a-class-from-cobject.md).

Por ejemplo, podría convertir un puntero a `CMyDoc`, llamado `pMyDoc`, en un puntero a `CDocument` mediante la siguiente expresión:

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

Si `pMyDoc` no apunta a un objeto derivado directa o indirectamente `CDocument`, la macro se producirá una aserción.

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
