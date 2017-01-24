---
title: "WeakRef (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::WeakRef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WeakRef (clase)"
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
caps.latest.revision: 10
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WeakRef (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Representa una *referencia débil* que solo puede usar Windows en tiempo de ejecución, no COM clásico. Una referencia débil representa un objeto que puede ser o no accesible.  
  
## Sintaxis  
  
```  
class WeakRef : public ComPtr<IWeakReference>  
```  
  
## Comentarios  
 Un objeto WeakRef mantiene una *referencia segura*, asociada a un objeto y puede ser o no válida. Llame al método As\(\) o AsIID\(\) para obtener una referencia segura. Cuando la referencia segura se válida, puede obtener acceso al objeto asociado. Cuando la referencia segura no es válida \(`nullptr`\), el objeto asociado es inaccesible.  
  
 Un objeto WeakRef se usa normalmente para representar un objeto cuya existencia se controla mediante una aplicación o un subproceso externo. Por ejemplo, construya un objeto de WeakRef a partir de una referencia a un objeto de archivo. Mientras el archivo esté abierto, la referencia segura será válida. Sin embargo, si el archivo está abierto, la referencia segura no será válida.  
  
 Tenga en cuenta que hay un cambio de comportamiento en los métodos [As](../windows/weakref-as-method.md), [AsIID](../windows/weakref-asiid-method.md) y [CopyTo](../windows/weakref-copyto-method.md) en el SDK de Windows 10. Anteriormente, después de llamar a cualquiera de estos métodos, consulte la WeakRef para `nullptr` para determinar si se obtuvo correctamente una referencia segura, como en el código siguiente:  
  
```cpp  
WeakRef wr; strongComptrRef.AsWeak(&wr); // Now suppose that the object strongComPtrRef points to no longer exists // and the following code tries to get a strong ref from the weak ref: ComPtr<ISomeInterface> strongRef; HRESULT hr = wr.As(&strongRef); // This check won't work with the Windows 10 SDK version of the library. // Use the HRESULT from previous As() call instead. if(wr == nullptr) { wprintf(L"Couldn’t get strong ref!"); }  
  
```  
  
 El código anterior no funciona al usar el SDK de Windows 10 \(o posterior\). En su lugar, compruebe el HRESULT devuelto por el método As o AsIID, o compruebe el puntero que se pasó para `nullptr`.  
  
```cpp  
if (hr != S_OK) { wprintf(L"Couldn't get strong ref!"); }  
  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[WeakRef::WeakRef \(Constructor\)](../windows/weakref-weakref-constructor.md)|Inicializa una nueva instancia de la clase WeakRef.|  
|[WeakRef::~WeakRef \(Destructor\)](../windows/weakref-tilde-weakref-destructor.md)|Desinicializa la instancia actual de la clase WeakRef.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[WeakRef::As \(Método\)](../windows/weakref-as-method.md)|Establece el parámetro de puntero ComPtr especificado para representar la interfaz especificada.|  
|[WeakRef::AsIID \(Método\)](../windows/weakref-asiid-method.md)|Establece el parámetro de puntero ComPtr especificado para representar el id. de interfaz especificado.|  
|[WeakRef::CopyTo \(Método\)](../windows/weakref-copyto-method.md)|Asigna un puntero a una interfaz, si está disponible, para la variable de puntero especificada.|  
  
### Operadores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[WeakRef::operator& \(Operador\)](../Topic/WeakRef::operator&%20Operator.md)|Devuelve un objeto ComPtrRef que representa al objeto WeakRef actual.|  
  
## Jerarquía de herencia  
 `ComPtr`  
  
 `WeakRef`  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)