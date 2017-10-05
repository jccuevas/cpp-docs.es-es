---
title: _com_ptr_t (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_ptr_t
dev_langs:
- C++
helpviewer_keywords:
- _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
caps.latest.revision: 8
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 3979a33f095092c5cbaac91793c501e31304a6d4
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="comptrt-class"></a>_com_ptr_t (Clase)
**Específicos de Microsoft**  
  
 Un objeto `_com_ptr_t` encapsula un puntero de interfaz COM y se denomina puntero “inteligente”. Esta clase de plantilla administra la asignación de recursos y la desasignación con llamadas de función a la **IUnknown** funciones miembro: `QueryInterface`, `AddRef`, y **versión**.  
  
 Normalmente se hace referencia a un puntero inteligente por la definición typedef proporcionada por el **_COM_SMARTPTR_TYPEDEF** macro. Esta macro toma un nombre de interfaz y el IID, y declara una especialización de `_com_ptr_t` con el nombre de la interfaz más un sufijo de `Ptr`. Por ejemplo:  
  
```  
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));  
```  
  
 declara el `_com_ptr_t` especialización **IMyInterfacePtr**.  
  
 Un conjunto de [plantillas de función](../cpp/relational-function-templates.md), no los miembros de esta plantilla de clase, admite las comparaciones con un puntero inteligente en el lado derecho del operador de comparación.  
  
### <a name="construction"></a>Construcción  
  
|||  
|-|-|  
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|Construye un objeto `_com_ptr_t`.|  
  
### <a name="low-level-operations"></a>Operaciones de bajo nivel  
  
|||  
|-|-|  
|[AddRef](../cpp/com-ptr-t-addref.md)|Llamadas a la `AddRef` función miembro de **IUnknown** en el puntero de interfaz encapsulado.|  
|[Asociar](../cpp/com-ptr-t-attach.md)|Encapsula un puntero de interfaz sin formato del tipo de este puntero inteligente.|  
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|Crea una nueva instancia de un objeto, dado un **CLSID** o **ProgID**.|  
|[Desasociar](../cpp/com-ptr-t-detach.md)|Extrae y devuelve el puntero de interfaz encapsulado.|  
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|Se asocia a una instancia existente de un objeto, dado un **CLSID** o **ProgID**.|  
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|Devuelve el puntero de interfaz encapsulado.|  
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|Llamadas a la `QueryInterface` función miembro de **IUnknown** en el puntero de interfaz encapsulado.|  
|[Release](../cpp/com-ptr-t-release.md)|Llamadas a la **versión** función miembro de **IUnknown** en el puntero de interfaz encapsulado.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador =](../cpp/com-ptr-t-operator-equal.md)|Asigna un nuevo valor a un objeto `_com_ptr_t` existente.|  
|[los operadores ==,! =, \<, >, \<=, > =](../cpp/com-ptr-t-relational-operators.md)|Compara el objeto de puntero inteligente con otro puntero inteligente, puntero de interfaz sin formato, o **NULL**.|  
|[Extractores de datos](../cpp/com-ptr-t-extractors.md)|Extrae el puntero de interfaz COM encapsulado.|  
  
**FIN de Específicos de Microsoft**  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** comip.h  
  
 **Lib:** omsuppw.lib o comsuppwd.lib (vea [/Zc: wchar_t (wchar_t es tipo nativo)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obtener más información)  
  
## <a name="see-also"></a>Vea también  
 [Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)
