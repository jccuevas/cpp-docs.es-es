---
title: "Especificadores de invalidaci&#243;n (Extensiones de componentes de C++) | Microsoft Docs"
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
  - "especificadores de invalidación, Visual C++"
  - "especificadores de invalidación"
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Especificadores de invalidaci&#243;n (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los *especificadores de invalidación* modifican la forma en que se comportan los tipos heredados y los miembros de tipos heredados en los tipos derivados.  
  
## Todos los runtimes  
 **Comentarios**  
  
 Para obtener más información acerca de los especificadores de invalidación, vea:  
  
-   [abstract](../windows/abstract-cpp-component-extensions.md)  
  
-   [new \(nueva ranura en vtable\)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
-   [override](../windows/override-cpp-component-extensions.md)  
  
-   [sealed](../windows/sealed-cpp-component-extensions.md)  
  
-   [Especificadores de invalidación y compilaciones nativas](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)  
  
 `abstract` y `sealed` también son válidos en declaraciones de tipos, donde no actúan como especificadores de invalidación.  
  
 Para obtener información acerca de cómo reemplazar explícitamente funciones de clase base, vea [Invalidaciones explícitas](../windows/explicit-overrides-cpp-component-extensions.md).  
  
## Windows en tiempo de ejecución  
 \(No hay notas para esta característica de lenguaje que solo se apliquen a Windows en tiempo de ejecución\).  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## Common Language Runtime  
 \(No hay notas para esta característica de lenguaje que solo se apliquen a Common Language Runtime\).  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)