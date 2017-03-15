---
title: "MakeAndInitialize (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::MakeAndInitialize"
dev_langs: 
  - "C++"
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# MakeAndInitialize (Funci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inicializa la clase especificada de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] .  Utilice esta función para crear instancias de un componente que se define en el mismo módulo.  
  
## Sintaxis  
  
```cpp  
template <typename T, typename I,   
typename TArg1,   
typename TArg2,   
typename TArg3,   
typename TArg4,   
typename TArg5,   
typename TArg6,   
typename TArg7,   
typename TArg8,   
typename TArg9> HRESULT MakeAndInitialize(_Outptr_result_nullonfailure_ I** ppvObject, TArg1 &&arg1, TArg2 &&arg2, TArg3 &&arg3, TArg4 &&arg4, TArg5 &&arg5, TArg6 &&arg6, TArg7 &&arg7, TArg8 &&arg8, TArg9 &&arg9) throw()  
  
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
 Valor `HRESULT`.  
  
## Comentarios  
 Vea [Cómo: Crear instancias de componentes WRL directamente](../windows/how-to-instantiate-wrl-components-directly.md) para obtener información sobre las diferencias entre esta función y [Microsoft::WRL::Make](../windows/make-function.md), y un ejemplo.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)