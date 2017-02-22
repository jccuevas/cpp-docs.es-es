---
title: "Make (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Make"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Make (función)"
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# Make (Funci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inicializa la clase especificada de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] .  Utilice esta función para crear instancias de un componente que se define en el mismo módulo.  
  
## Sintaxis  
  
```  
template <  
   typename T,  
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
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6,  
   TArg7 &&arg7,  
   TArg8 &&arg8,  
   TArg9 &&arg9  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7,  
   typename TArg8  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6,  
   TArg7 &&arg7,  
   TArg8 &&arg8  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6,  
   typename TArg7  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6,  
   TArg7 &&arg7  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5,  
   typename TArg6  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5,  
   TArg6 &&arg6  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4,  
   typename TArg5  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4,  
   TArg5 &&arg5  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3,  
   typename TArg4  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3,  
   TArg4 &&arg4  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2,  
   typename TArg3  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2,  
   TArg3 &&arg3  
);  
template <  
   typename T,  
   typename TArg1,  
   typename TArg2  
>  
ComPtr<T> Make(  
   TArg1 &&arg1,  
   TArg2 &&arg2  
);  
template <  
   typename T,  
   typename TArg1  
>  
ComPtr<T> Make(  
   TArg1 &&arg1  
);  
template <  
   typename T  
>  
ComPtr<T> Make();  
```  
  
#### Parámetros  
 `T`  
 Una clase definida por el usuario que hereda de `WRL::RuntimeClass`.  
  
 `TArg1`  
 Tipo de argumento 1 que se pasa a la clase especificada en tiempo de ejecución.  
  
 `TArg2`  
 Tipo de argumento 2 que se pasa a la clase especificada en tiempo de ejecución.  
  
 `TArg3`  
 Tipo de argumento 3 que se pasa a la clase especificada en tiempo de ejecución.  
  
 `TArg4`  
 Tipo de argumento 4 que se pasa a la clase especificada en tiempo de ejecución.  
  
 `TArg5`  
 Tipo de argumento 5 que se pasa a la clase especificada en tiempo de ejecución.  
  
 `TArg6`  
 Tipo de argumento 6 que se pasa a la clase especificada en tiempo de ejecución.  
  
 `TArg7`  
 Tipo de argumento 7 que se pasa a la clase especificada en tiempo de ejecución.  
  
 `TArg8`  
 Tipo de argumento 8 que se pasa a la clase especificada en tiempo de ejecución.  
  
 `TArg9`  
 Tipo de argumento 9 que se pasa a la clase especificada en tiempo de ejecución.  
  
 `arg1`  
 Argumento 1 que se pasa a la clase especificada en tiempo de ejecución.  
  
 `arg2`  
 Argumento 2 que se pasa a la clase especificada en tiempo de ejecución.  
  
 `arg3`  
 Argumento 3 que se pasa a la clase especificada en tiempo de ejecución.  
  
 `arg4`  
 Argumento 4 que se pasa a la clase especificada en tiempo de ejecución.  
  
 `arg5`  
 Argumento 5 que se pasa a la clase especificada en tiempo de ejecución.  
  
 `arg6`  
 Argumento 6 que se pasa a la clase especificada en tiempo de ejecución.  
  
 `arg7`  
 Argumento 7 que se pasa a la clase especificada en tiempo de ejecución.  
  
 `arg8`  
 Argumento 8 que se pasa a la clase especificada en tiempo de ejecución.  
  
 `arg9`  
 Argumento 9 que se pasa a la clase especificada en tiempo de ejecución.  
  
## Valor devuelto  
 Un objeto de `ComPtr<T>` si correctamente; si no, `nullptr`.  
  
## Comentarios  
 Vea [Cómo: Crear instancias de componentes WRL directamente](../windows/how-to-instantiate-wrl-components-directly.md) para obtener información sobre las diferencias entre esta función y [Microsoft::WRL::Details::MakeAndInitialize](../windows/makeandinitialize-function.md), y un ejemplo.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)