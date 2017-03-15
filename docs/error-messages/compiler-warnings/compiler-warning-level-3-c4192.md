---
title: "Advertencia del compilador (nivel 3) C4192 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4192"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4192"
ms.assetid: ea5f91fa-8c96-4f3f-ac42-0c8a86d4e5df
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 3) C4192
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se excluye 'nombre' de forma automática al importar la biblioteca de tipos 'biblioteca'  
  
 Una biblioteca `#import` contiene un elemento, *nombre,* que también está definido en los encabezados de sistema Win32.  Debido a las limitaciones de las bibliotecas de tipos, los nombres como **IUnknown** o GUID se definen a menudo en una biblioteca de tipos, duplicando la definición de los encabezados de sistema.  `#import` detecta estos elementos pero no los incorpora en los archivos de encabezado .tlh y .tli.  
  
 Para evitarlo, utilice los atributos de `#import` [no\_auto\_exclude](../../preprocessor/no-auto-exclude.md) e [include\(\)](../../preprocessor/include-parens.md).