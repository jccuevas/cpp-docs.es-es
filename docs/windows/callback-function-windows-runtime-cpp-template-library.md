---
title: "Función de devolución de llamada (biblioteca de plantillas C++ de Windows en tiempo de ejecución) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Callback
dev_langs:
- C++
ms.assetid: afb15d25-3230-44f7-b321-e17c54872943
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2b2d83096ce4e6ff9245a9e26516d6a487155695
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="callback-function-windows-runtime-c-template-library"></a>Callback (Función) (Biblioteca de plantillas C++ de Windows en tiempo de ejecución)
Crea un objeto cuya función de miembro es un método de devolución de llamada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<  
   typename TDelegateInterface,  
   typename TCallback  
>  
ComPtr<TDelegateInterface> Callback(  
   TCallbackcallback  
);  
template<  
   typename TDelegateInterface,  
   typename TCallbackObject  
>  
ComPtr<TDelegateInterface> Callback(  
   _In_ TCallbackObject *object,  
   _In_ HRESULT (TCallbackObject::* method)()  
);  
template<  
   typename TDelegateInterface,  
   typename TCallbackObject,  
   typename TArg1  
>  
ComPtr<TDelegateInterface> Callback(  
   _In_ TCallbackObject *object,  
   _In_ HRESULT (TCallbackObject::* method)(TArg1)  
);  
template<  
   typename TDelegateInterface,  
   typename TCallbackObject,  
   typename TArg1,  
   typename TArg2  
>  
ComPtr<TDelegateInterface> Callback(  
   _In_ TCallbackObject *object,  
   _In_ HRESULT (TCallbackObject::* method)(TArg1,  
   TArg2)  
);  
template<  
   typename TDelegateInterface,  
   typename TCallbackObject,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3  
>  
ComPtr<TDelegateInterface> Callback(  
   _In_ TCallbackObject *object,  
   _In_ HRESULT (TCallbackObject::* method)(TArg1,  
   TArg2,  
   TArg3)  
);  
template<  
   typename TDelegateInterface,  
   typename TCallbackObject,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4  
>  
ComPtr<TDelegateInterface> Callback(  
   _In_ TCallbackObject *object,  
   _In_ HRESULT (TCallbackObject::* method)(TArg1,  
   TArg2,  
   TArg3,  
   TArg4)  
);  
template<  
   typename TDelegateInterface,  
   typename TCallbackObject,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5  
>  
ComPtr<TDelegateInterface> Callback(  
   _In_ TCallbackObject *object,  
   _In_ HRESULT (TCallbackObject::* method)(TArg1,  
   TArg2,  
   TArg3,  
   TArg4,  
   TArg5)  
);  
template<  
   typename TDelegateInterface,  
   typename TCallbackObject,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6  
>  
ComPtr<TDelegateInterface> Callback(  
   _In_ TCallbackObject *object,  
   _In_ HRESULT (TCallbackObject::* method)(TArg1,  
   TArg2,  
   TArg3,  
   TArg4,  
   TArg5,  
   TArg6)  
);  
template<  
   typename TDelegateInterface,  
   typename TCallbackObject,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7  
>  
ComPtr<TDelegateInterface> Callback(  
   _In_ TCallbackObject *object,  
   _In_ HRESULT (TCallbackObject::* method)(TArg1,  
   TArg2,  
   TArg3,  
   TArg4,  
   TArg5,  
   TArg6,  
   TArg7)  
);  
template<  
   typename TDelegateInterface,  
   typename TCallbackObject,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7,  
   typename TArg8  
>  
ComPtr<TDelegateInterface> Callback(  
   _In_ TCallbackObject *object,  
   _In_ HRESULT (TCallbackObject::* method)(TArg1,  
   TArg2,  
   TArg3,  
   TArg4,  
   TArg5,  
   TArg6,  
   TArg7,  
   TArg8)  
);  
template<  
   typename TDelegateInterface,  
   typename TCallbackObject,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7,  
   typename TArg8,  
   typename TArg9  
>  
ComPtr<TDelegateInterface> Callback(  
   _In_ TCallbackObject *object,  
   _In_ HRESULT (TCallbackObject::* method)(TArg1,  
   TArg2,  
   TArg3,  
   TArg4,  
   TArg5,  
   TArg6,  
   TArg7,  
   TArg8,  
   TArg9)  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `TDelegateInterface`  
 Un parámetro de plantilla que especifica la interfaz del delegado al que se llamará cuando se produzca un evento.  
  
 `TCallback`  
 Un parámetro de plantilla que especifica el tipo de un objeto que representa un objeto y su función miembro de devolución de llamada.  
  
 `TCallbackObject`  
 Un parámetro de plantilla que especifica el objeto cuya función miembro es el método al que se debe llamar cuando se produce un evento.  
  
 `TArg1`  
 Un parámetro de plantilla que especifica el tipo del primer argumento del método de devolución de llamada.  
  
 `TArg2`  
 Un parámetro de plantilla que especifica el tipo del segundo argumento del método de devolución de llamada.  
  
 `TArg3`  
 Un parámetro de plantilla que especifica el tipo del tercer argumento del método de devolución de llamada.  
  
 `TArg4`  
 Un parámetro de plantilla que especifica el tipo del cuarto argumento del método de devolución de llamada.  
  
 `TArg5`  
 Un parámetro de plantilla que especifica el tipo del quinto argumento del método de devolución de llamada.  
  
 `TArg6`  
 Un parámetro de plantilla que especifica el tipo del sexto argumento del método de devolución de llamada.  
  
 `TArg7`  
 Un parámetro de plantilla que especifica el tipo del séptimo argumento del método de devolución de llamada.  
  
 `TArg8`  
 Un parámetro de plantilla que especifica el tipo del octavo argumento del método de devolución de llamada.  
  
 `TArg9`  
 Un parámetro de plantilla que especifica el tipo del noveno argumento del método de devolución de llamada.  
  
 `callback`  
 Un objeto que representa el objeto de devolución de llamada y su función miembro.  
  
 `object`  
 El objeto a cuya función miembro se llama cuando se produce un evento.  
  
 `method`  
 La función miembro a la que se llamará cuando se produzca un evento.  
  
## <a name="return-value"></a>Valor devuelto  
 Un objeto cuya función miembro es el método de devolución de llamada especificado.  
  
## <a name="remarks"></a>Comentarios  
 La base de un objeto delegado debe ser IUnknown, no IInspectable.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [Microsoft::WRL (espacio de nombres)](../windows/microsoft-wrl-namespace.md)