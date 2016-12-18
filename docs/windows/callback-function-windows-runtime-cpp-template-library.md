---
title: "Callback (Funci&#243;n) (Biblioteca de plantillas C++ de Windows en tiempo de ejecuci&#243;n) | Microsoft Docs"
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
  - "event/Microsoft::WRL::Callback"
dev_langs: 
  - "C++"
ms.assetid: afb15d25-3230-44f7-b321-e17c54872943
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Callback (Funci&#243;n) (Biblioteca de plantillas C++ de Windows en tiempo de ejecuci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea un objeto cuya función de miembro es un método de devolución de llamada.  
  
## Sintaxis  
  
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
  
#### Parámetros  
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
  
## Valor devuelto  
 Un objeto cuya función miembro es el método de devolución de llamada especificado.  
  
## Comentarios  
 La base de un objeto delegado debe ser IUnknown, no IInspectable.  
  
## Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)