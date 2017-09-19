---
title: "Tipo de conversión de objetos de clase MFC | Documentos de Microsoft"
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
- macros, type casting
- pointers, type casting
- type casts
- casting types
- macros, casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
caps.latest.revision: 15
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: f1ae094e7085017f03daab3f73323da13ab1be39
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="type-casting-of-mfc-class-objects"></a>Conversión de tipos de objetos de clase de MFC
Macros de conversión de tipo proporcionan una manera de convertir un puntero a un puntero que señala a un objeto de una clase específica, con o sin comprobar que la conversión es legal determinado.  
  
 La tabla siguiente enumeran las macros de conversión de tipo MFC.  
  
### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>Macros que conversión los punteros a objetos de clase MFC  
  
|||  
|-|-|  
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|Convierte un puntero a un puntero a un objeto de clase al comprobar si la conversión es válida.|  
|[STATIC_DOWNCAST](#static_downcast)|Convierte un puntero a un objeto de una clase a un puntero de un tipo relacionado. En una compilación de depuración hace un **ASSERT** si el objeto no es un "tipo de" el tipo de destino.|  
  
##  <a name="dynamic_downcast"></a>DYNAMIC_DOWNCAST  
 Proporciona una forma práctica para convertir un puntero a un puntero a un objeto de clase al comprobar si la conversión es válida.  
  
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
 Conversiones *pobject* a un puntero a un *class_name* objeto.  
  
```   
STATIC_DOWNCAST(class_name, pobject)   
```  
  
### <a name="parameters"></a>Parámetros  
 *CLASS_NAME*  
 El nombre de la clase que se va a convertir a.  
  
 *pObject*  
 El puntero se convierte en un puntero a un *class_name* objeto.  
  
### <a name="remarks"></a>Comentarios  
 *pObject* debe ser **NULL**, o seleccione un objeto de una clase derivada directa o indirectamente, de *class_name*. En las compilaciones de su aplicación con el **_DEBUG** definido el símbolo de preprocesador, la macro le **ASSERT** si *pobject* no es **NULL**, o apunta a un objeto que no es un "tipo de" la clase especificada en el *class_name* parámetro (consulte [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof)). No- **_DEBUG** compilaciones, la macro se realiza la conversión sin ninguna comprobación de tipos.  
  
 La clase especificada en el *class_name* parámetro debe derivarse de `CObject` y deben utilizar la `DECLARE_DYNAMIC` y `IMPLEMENT_DYNAMIC`, el `DECLARE_DYNCREATE` y `IMPLEMENT_DYNCREATE`, o la `DECLARE_SERIAL` y `IMPLEMENT_SERIAL` macros como se explica en el artículo [CObject (clase): derivar una clase de CObject](../../mfc/deriving-a-class-from-cobject.md).  
  
 Por ejemplo, podría convertir un puntero a `CMyDoc`, llamado `pMyDoc`, un puntero a **CDocument** mediante la siguiente expresión:  
  
 [!code-cpp[NVC_MFCDocView&#197;](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]  
  
 Si `pMyDoc` no señala a un objeto que se deriva directa o indirectamente de **CDocument**, la macro le **ASSERT**.  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)

