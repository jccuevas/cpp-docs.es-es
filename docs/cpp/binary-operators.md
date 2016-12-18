---
title: "Operadores binarios | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operadores binarios"
  - "operadores de selección de miembros"
  - "operadores [C++], binaria"
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operadores binarios
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En la tabla siguiente se muestra una lista de operadores que se pueden sobrecargar.  
  
### Operadores binarios redefinibles  
  
|Operador|Nombre|  
|--------------|------------|  
|**,**|Coma|  
|`!=`|Desigualdad|  
|`%`|Módulo|  
|`%=`|Módulo\/asignación|  
|**&**|AND bit a bit|  
|**&&**|AND lógico|  
|**&\=**|AND bit a bit\/asignación|  
|**\***|Multiplicación|  
|**\*\=**|Multiplicación\/asignación|  
|**\+**|Adición|  
|`+=`|Suma\/asignación|  
|**–**|Resta|  
|**–\=**|Resta\/asignación|  
|**–\>**|Selección de miembro|  
|**–\>\***|Selección de puntero a miembro|  
|**\/**|División|  
|`/=`|División\/asignación|  
|**\<**|Menor que|  
|**\<\<**|Desplazamiento a la izquierda|  
|**\<\<\=**|Desplazamiento a la izquierda\/asignación|  
|**\<\=**|Menor o igual que|  
|**\=**|Asignación|  
|`==`|Igualdad|  
|**\>**|Mayor que|  
|**\>\=**|Mayor o igual que|  
|**\>\>**|Desplazamiento a la derecha|  
|**\>\>\=**|Desplazamiento a la derecha\/asignación|  
|**^**|OR exclusivo|  
|`^=`|OR exclusivo\/asignación|  
|**&#124;**|OR inclusivo bit a bit|  
|`&#124;=`|OR inclusivo bit a bit\/asignación|  
|`&#124;&#124;`|OR lógico|  
  
 Para declarar una función de operador binario como miembro no estático, debe declararla de la forma siguiente:  
  
 *ret\-type* **operador**`op`**\(** `arg` **\)**  
  
 donde *ret\-type* es el tipo devuelto, `op` es uno de los operadores que aparecen en la tabla anterior y `arg` es un argumento de cualquier tipo.  
  
 Para declarar una función de operador binario como función global, debe declararla de la forma siguiente:  
  
 *ret\-type* **operator**`op`**\(** `arg1`**,** `arg2` **\)**  
  
 donde *ret\-type* y `op` son como se describen para las funciones de operador de miembro y `arg1` y `arg2` son argumentos.  Al menos uno de los argumentos debe ser de tipo de clase.  
  
> [!NOTE]
>  No hay restricciones para los tipos de valor devuelto de los operadores binarios; sin embargo, la mayoría de los operadores binarios definidos por el usuario devuelven un tipo de clase o una referencia a un tipo de clase.  
  
## Vea también  
 [Sobrecarga de operadores](../cpp/operator-overloading.md)