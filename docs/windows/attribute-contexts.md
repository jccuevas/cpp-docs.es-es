---
title: "Attribute Contexts | Microsoft Docs"
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
  - "attributes [C++], contexts"
ms.assetid: 3086351f-77a8-4048-99e9-3b6b041b9437
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Attribute Contexts
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los atributos de C\+\+ se puede describir utilizando cuatro campos básicos: el destino se pueden aplicar a \(**Se aplica a**\), si ambos son repetibles o no \(**repetible**\), la presencia necesaria de otros atributos \(**Atributos necesarios**\), y las incompatibilidades con otros atributos \(**Atributos no válidos**\).  Estos campos se muestran en un cuadro adjunto en el tema de referencia de cada atributo.  Estos campos se describe a continuación.  
  
## Se aplica a  
 Este campo describe los diferentes elementos del lenguaje C\+\+ que son destinos válidos para el atributo especificado.  Por ejemplo, si un atributo especifica la “clase” en el campo de **Se aplica a** , esto indica que el atributo sólo se puede aplicar a una clase válida de C\+\+.  Si el atributo se aplica a una función miembro de una clase, un error de sintaxis resultaría.  
  
 Para obtener más información, vea [Atributos por Uso](../windows/attributes-by-usage.md).  
  
## repetible  
 Este campo indica si el atributo se puede aplicar repetidamente al mismo destino.  la mayoría de atributos no es repetible.  
  
## Atributos necesarios  
 Este listas de campos otros atributos que deben estar presentes \(es decir, aplicado al mismo destino\) para que el atributo especificado correctamente.  Es raro que un atributo tiene cualquier entrada para este campo.  
  
## Atributos no válidos  
 este listas de campos otros atributos que son incompatibles con el atributo especificado.  Es raro que un atributo tiene cualquier entrada para este campo.  
  
## Vea también  
 [C\+\+ Attributes Reference](../windows/cpp-attributes-reference.md)