---
title: "component | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.component"
  - "component_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "component (pragma)"
  - "pragma (directivas), componente"
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# component
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Controla la recopilación de información de examen o información de dependencia en los archivos de código fuente.  
  
## Sintaxis  
  
```  
  
      #pragma component( browser, { on | off }[, references [, name ]] )  
#pragma component( minrebuild, on | off )  
#pragma component( mintypeinfo, on | off )  
```  
  
## Comentarios  
  
## Explorador  
 Puede activar o desactivar la recopilación, así como especificar que determinados nombres se omitan al recopilar la información.  
  
 El uso de on u off controla la recopilación de información de examen de la pragma hacia delante.  Por ejemplo:  
  
```  
#pragma component(browser, off)  
```  
  
 detiene la recopilación de información de examen por parte del compilador.  
  
> [!NOTE]
>  Para activar la recopilación de información de examen con esta pragma, [debe estar habilitada la información de examen](../build/reference/building-browse-information-files-overview.md).  
  
 La opción **references** se puede utilizar con o sin el argumento *name*.  El uso de **references** sin *name* activa o desactiva la recopilación de referencias \(sin embargo, continúa la recopilación de otra información de examen\).  Por ejemplo:  
  
```  
#pragma component(browser, off, references)  
```  
  
 detiene la recopilación de información de referencia por parte del compilador.  
  
 El uso de **references** con *name* y **off** impide que aparezcan referencias a *name* en la ventana de información de examen.  Utilice esta sintaxis para omitir nombres y tipos en los que no esté interesado y reducir el tamaño de los archivos de información de examen.  Por ejemplo:  
  
```  
#pragma component(browser, off, references, DWORD)  
```  
  
 omite referencias a **DWORD** desde ese punto hacia delante.  Puede volver a activar la recopilación de referencias a `DWORD` utilizando **on**:  
  
```  
#pragma component(browser, on, references, DWORD)  
```  
  
 Esta es el único medio para reanudar la recopilación de referencias a *name*; debe activar explícitamente cualquier argumento *name* que haya desactivado.  
  
 Para evitar que el preprocesador expanda *name* \(por ejemplo, que expanda **NULL** a **0**\), inclúyalo entre comillas:  
  
```  
#pragma component(browser, off, references, "NULL")  
```  
  
## Recompilación mínima  
 La característica de recompilación mínima de Visual C\+\+ requiere que el compilador cree y almacene la información de dependencia de clase de C\+\+, que ocupa espacio en disco.  Para ahorrar espacio en disco, puede utilizar `#pragma component( minrebuild, off )` siempre que no necesite recopilar información de dependencia, por ejemplo, en archivos de encabezado inalterados.  Para volver a activar la recopilación de información de dependencia, debe insertar `#pragma component(minrebuild, on)` después de las clases inalteradas.  
  
## Reducción de la información de tipo  
 La opción **mintypeinfo** reduce la información de depuración para la región especificada.  El volumen de esta información es considerable, afectando a los archivos .pdb y .obj.  No puede depurar clases ni estructuras en la región correspondiente a mintypeinfo.  El uso de la opción mintypeinfo puede ser útil para evitar la advertencia siguiente:  
  
```  
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information  
```  
  
 Para obtener más información, vea la opción del compilador \(\/Gm\) [Habilitar recompilación mínima](../build/reference/gm-enable-minimal-rebuild.md).  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)