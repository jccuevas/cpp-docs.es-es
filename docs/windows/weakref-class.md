---
title: WeakRef (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::WeakRef
dev_langs: C++
helpviewer_keywords: WeakRef class
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 148c39f1ef38b6b20de6d50cc75352a4f30a9090
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="weakref-class"></a>WeakRef (Clase)
Representa una *referencia débil* que solo puede usar Windows en tiempo de ejecución, no COM clásico. Una referencia débil representa un objeto que puede ser o no accesible.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class WeakRef : public ComPtr<IWeakReference>  
```  
  
## <a name="remarks"></a>Comentarios  
 Un objeto WeakRef mantiene una *referencia segura*, asociada a un objeto y puede ser o no válida. Llame al método As() o AsIID() para obtener una referencia segura. Cuando la referencia segura se válida, puede obtener acceso al objeto asociado. Cuando la referencia segura no es válida (`nullptr`), el objeto asociado es inaccesible.  
  
 Un objeto WeakRef se usa normalmente para representar un objeto cuya existencia se controla mediante una aplicación o un subproceso externo. Por ejemplo, construya un objeto de WeakRef a partir de una referencia a un objeto de archivo. Mientras el archivo esté abierto, la referencia segura será válida. Sin embargo, si el archivo está abierto, la referencia segura no será válida.  
  
 Tenga en cuenta que hay un cambio de comportamiento en los métodos [As](../windows/weakref-as-method.md), [AsIID](../windows/weakref-asiid-method.md) y [CopyTo](../windows/weakref-copyto-method.md) en el SDK de Windows 10. Anteriormente, después de llamar a cualquiera de estos métodos, consulte la WeakRef para `nullptr` para determinar si se obtuvo correctamente una referencia segura, como en el código siguiente:  
  
```cpp  
WeakRef wr;  
strongComptrRef.AsWeak(&wr);  
  
// Now suppose that the object strongComPtrRef points to no longer exists  
// and the following code tries to get a strong ref from the weak ref:  
ComPtr<ISomeInterface> strongRef;  
HRESULT hr = wr.As(&strongRef);  
  
// This check won't work with the Windows 10 SDK version of the library.  
// Check the input pointer instead.  
if(wr == nullptr)  
{  
    wprintf(L"Couldn’t get strong ref!");  
}  
  
```  
  
 El código anterior no funciona al usar el SDK de Windows 10 (o posterior). En su lugar, compruebe el puntero que se pasó para `nullptr`.  
  
```cpp  
if (strongRef == nullptr)  
{  
    wprintf(L"Couldn't get strong ref!");  
 }  
  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[WeakRef::WeakRef (constructor)](../windows/weakref-weakref-constructor.md)|Inicializa una nueva instancia de la clase WeakRef.|  
|[WeakRef::~WeakRef (destructor)](../windows/weakref-tilde-weakref-destructor.md)|Desinicializa la instancia actual de la clase WeakRef.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[WeakRef::As (método)](../windows/weakref-as-method.md)|Establece el parámetro de puntero ComPtr especificado para representar la interfaz especificada.|  
|[WeakRef::AsIID (método)](../windows/weakref-asiid-method.md)|Establece el parámetro de puntero ComPtr especificado para representar el id. de interfaz especificado.|  
|[WeakRef::CopyTo (método)](../windows/weakref-copyto-method.md)|Asigna un puntero a una interfaz, si está disponible, para la variable de puntero especificada.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[WeakRef::operator& (operador)](../windows/weakref-operator-ampersand-operator.md)|Devuelve un objeto ComPtrRef que representa al objeto WeakRef actual.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ComPtr`  
  
 `WeakRef`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)