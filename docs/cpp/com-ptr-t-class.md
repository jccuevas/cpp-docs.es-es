---
title: "_com_ptr_t (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_ptr_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_com_ptr_t (clase)"
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# _com_ptr_t (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Un objeto `_com_ptr_t` encapsula un puntero de interfaz COM y se denomina puntero “inteligente”.  Esta clase de plantilla administra la asignación de recursos y la desasignación con llamadas a función a las funciones miembro de **IUnknown**: `QueryInterface`, `AddRef` y **Release**.  
  
 La definición typedef proporcionada por la macro **\_COM\_SMARTPTR\_TYPEDEF** normalmente hace referencia a un puntero inteligente.  Esta macro toma un nombre de interfaz y el IID, y declara una especialización de `_com_ptr_t` con el nombre de la interfaz más un sufijo de `Ptr`.  Por ejemplo:  
  
```  
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));  
```  
  
 declara la especialización **IMyInterfacePtr**de `_com_ptr_t`.  
  
 Un conjunto de [plantillas de función](../cpp/relational-function-templates.md), no miembros de esta clase de plantilla, admite las comparaciones con un puntero inteligente a la derecha del operador de comparación.  
  
### Construcción  
  
|||  
|-|-|  
|[\_com\_ptr\_t](../cpp/com-ptr-t-com-ptr-t.md)|Construye un objeto `_com_ptr_t`.|  
  
### Operaciones de bajo nivel  
  
|||  
|-|-|  
|[AddRef](../cpp/com-ptr-t-addref.md)|Llama a la función miembro `AddRef` de **IUnknown** en el puntero de interfaz encapsulado.|  
|[Attach](../cpp/com-ptr-t-attach.md)|Encapsula un puntero de interfaz sin formato del tipo de este puntero inteligente.|  
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|Crea una nueva instancia de un objeto, dado un **CLSID** o **ProgID**.|  
|[Desasociar](../cpp/com-ptr-t-detach.md)|Extrae y devuelve el puntero de interfaz encapsulado.|  
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|Se adjunta a una instancia existente de un objeto, dado un **CLSID** o **ProgID**.|  
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|Devuelve el puntero de interfaz encapsulado.|  
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|Llama a la función miembro `QueryInterface` de **IUnknown** en el puntero de interfaz encapsulado.|  
|[Release](../cpp/com-ptr-t-release.md)|Llama a la función miembro **Release** de **IUnknown** en el puntero de interfaz encapsulado.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../cpp/com-ptr-t-operator-equal.md)|Asigna un nuevo valor a un objeto `_com_ptr_t` existente.|  
|[operadores \=\=, \!\=, \<, \>, \<\=, \>\=](../cpp/com-ptr-t-relational-operators.md)|Compara el objeto de puntero inteligente con otro puntero inteligente, puntero de interfaz sin formato o **NULL**.|  
|[Extractores](../cpp/com-ptr-t-extractors.md)|Extrae el puntero de interfaz COM encapsulado.|  
  
## FIN de Específicos de Microsoft  
  
## Requisitos  
 **Encabezado:** comip.h  
  
 **Lib:** omsuppw.lib o comsuppwd.lib \(vea [\/Zc:wchar\_t \(wchar\_t es un tipo nativo\)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) para obtener más información\)  
  
## Vea también  
 [Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)