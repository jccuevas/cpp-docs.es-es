---
title: "El espacio de nombres ra&#237;z &lt;espacioDeNombres&gt; no es conforme a CLS | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40038"
  - "vbc40038"
helpviewer_keywords: 
  - "BC40038"
ms.assetid: ec850295-b2fe-4f19-b808-d22fe0aaa32d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El espacio de nombres ra&#237;z &lt;espacioDeNombres&gt; no es conforme a CLS
Un ensamblado está marcado como `<CLSCompliant(True)>`, pero el nombre del espacio de nombres raíz comienza con un carácter de subrayado \(`_`\).  
  
 Un elemento de programación puede contener uno o más caracteres de subrayado, pero para ser conforme a [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) no debe comenzar con un carácter de subrayado. Vea [Nombres de elementos declarados](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md).  
  
 Al aplicar <xref:System.CLSCompliantAttribute> a un elemento de programación, establezca el parámetro `isCompliant` del atributo en `True` o `False` para indicar conformidad o disconformidad. No hay ningún valor predeterminado para este parámetro y debe proporcionar un valor.  
  
 Si no se aplica <xref:System.CLSCompliantAttribute> a un elemento, se considera que no es conforme.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md).  
  
 **Identificador de error:** BC40038  
  
### Para corregir este error  
  
-   Si requiere conformidad con CLS, cambie el nombre del espacio de nombres raíz para que no comience con un carácter de subrayado.  
  
-   Si necesita mantener el nombre del espacio de nombres raíz, quite el <xref:System.CLSCompliantAttribute> del ensamblado o márquelo como `<CLSCompliant(False)>`.  
  
## Vea también  
 [Namespace \(Instrucción\)](../Topic/Namespace%20Statement.md)   
 [Espacios de nombres en Visual Basic](../Topic/Namespaces%20in%20Visual%20Basic.md)   
 [\/rootnamespace](../Topic/-rootnamespace.md)   
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: Cambiar el espacio de nombres de una aplicación \(Visual Basic\)](http://msdn.microsoft.com/es-es/029d85c0-e173-4f7a-afba-a29f3aaf6ebf)   
 [Nombres de elementos declarados](../Topic/Declared%20Element%20Names%20\(Visual%20Basic\).md)   
 [Convenciones de nomenclatura de Visual Basic](../Topic/Visual%20Basic%20Naming%20Conventions.md)   
 [\<PAVE OVER\> Escribir código conforme a CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3)