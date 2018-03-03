---
title: "Tipo de conversión de los objetos de clase MFC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.classes
dev_langs:
- C++
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fc887ad855b00b525c74b66bfc70f2adb3312e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="type-casting-of-mfc-class-objects"></a>Conversión de tipos de objetos de clase de MFC
Macros de conversión de tipo proporcionan una forma de convertir un puntero especificado a un puntero que señala a un objeto de clase específica, con o sin comprobar que la conversión es legal.  
  
 En la tabla siguiente se enumera las macros de conversión de tipo MFC.  
  
### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Macros que conversión punteros a objetos de clase MFC  
  
|||  
|-|-|  
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|Convierte un puntero a un puntero a un objeto de clase al comprobar para ver si la conversión es válida.|  
|[STATIC_DOWNCAST](#static_downcast)|Convierte un puntero a un objeto de una clase a un puntero de un tipo relacionado. En una compilación de depuración hace un **ASSERT** si el objeto no es un "tipo de" el tipo de destino.|  
  
##  <a name="dynamic_downcast"></a>DYNAMIC_DOWNCAST  
 Proporciona una forma práctica para convertir un puntero a un puntero a un objeto de clase al comprobar para ver si la conversión es válida.  
  
```   
DYNAMIC_DOWNCAST(class, pointer)  
```  
  
### <a name="parameters"></a>Parámetros  
 `class`  
 El nombre de una clase.  
  
 `pointer`  
 Un puntero a convertirse en un puntero a un objeto de tipo `class`.  
  
### <a name="remarks"></a>Comentarios  
 La macro proyectará la `pointer` parámetro a un puntero a un objeto de la `class` tipo del parámetro.  
  
 Si el objeto al que hace referencia el puntero es un "tipo de" la clase identificada, la macro devuelve el puntero adecuado. Si no es una conversión válidas, la macro devuelve **NULL**.  
  
##  <a name="static_downcast"></a>STATIC_DOWNCAST  
 Conversiones *pobject* en un puntero a un *class_name* objeto.  
  
```   
STATIC_DOWNCAST(class_name, pobject)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre de la clase que se convierte en.  
  
 *pObject*  
 El puntero se convierte en un puntero a un *class_name* objeto.  
  
### <a name="remarks"></a>Comentarios  
 *pObject* deben ser **NULL**, o seleccione un objeto de una clase que se deriva directamente, o indirectamente, de *class_name*. En las compilaciones de la aplicación con el **_DEBUG** definido por el símbolo de preprocesador, la macro le **ASSERT** si *pobject* no **NULL**, o Si señala a un objeto que no es un "tipo de" la clase especificada en el *class_name* parámetro (consulte [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof)). No- **_DEBUG** compilaciones, la macro realiza la conversión sin ninguna comprobación de tipos.  
  
 La clase especificada en el *class_name* parámetro debe derivarse de `CObject` y deben utilizar la `DECLARE_DYNAMIC` y `IMPLEMENT_DYNAMIC`, el `DECLARE_DYNCREATE` y `IMPLEMENT_DYNCREATE`, o `DECLARE_SERIAL` y `IMPLEMENT_SERIAL`macros tal como se describe en el artículo [CObject (clase): derivar una clase de CObject](../../mfc/deriving-a-class-from-cobject.md).  
  
 Por ejemplo, puede convertir un puntero a `CMyDoc`, llamado `pMyDoc`, en un puntero a **CDocument** mediante la siguiente expresión:  
  
 [!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]  
  
 Si `pMyDoc` no señala a un objeto que se derivan directa o indirectamente **CDocument**, la macro le **ASSERT**.  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)
