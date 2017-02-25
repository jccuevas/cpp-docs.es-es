---
title: "Creating Registrar Scripts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, Registro"
  - "registrar scripts [ATL]"
  - "scripting, registry scripting"
  - "scripts, crear"
  - "scripts, Registrar scripts"
ms.assetid: cbd5024b-8061-4a71-be65-7fee90374a35
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Creating Registrar Scripts
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un script de registro proporciona controlada por datos, en lugar de API\-controlado, acceso al registro del sistema.  el acceso controlado por datos suele ser más eficaz ya que únicamente acepta uno o dos líneas en un script para agregar una clave en el registro.  
  
 [Asistente para controles ATL](../atl/reference/atl-control-wizard.md) genera automáticamente un script de registro del servidor COM.  Puede encontrar este script en el archivo .rgs asociado al objeto.  
  
 El motor de script de registro ATL procesa el script de registro en tiempo de ejecución.  ATL invoca automáticamente el motor de scripts durante la instalación del servidor.  
  
 En este artículo se tratan los siguientes temas relacionados con los scripts del registro:  
  
-   [Sintaxis de comprender el formulario de Backus \(BNF\) Nauer](../atl/understanding-backus-nauer-form-bnf-syntax.md)  
  
-   [Árbol de análisis sintácticas de introducción](../atl/understanding-parse-trees.md)  
  
-   [Ejemplos de script de registro](../atl/registry-scripting-examples.md)  
  
-   [Usar parámetros reemplazables \(el preprocesador de registro\)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)  
  
-   [Invocar scripts](../atl/invoking-scripts.md)  
  
## Vea también  
 [Componente de registro \(Registrador\)](../atl/atl-registry-component-registrar.md)