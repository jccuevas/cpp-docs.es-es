---
title: "Directivas de plantilla | Microsoft Docs"
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
  - "[!else] (directiva de plantilla)"
  - "[!endif] (directiva de plantilla)"
  - "[!endloop] (directiva de plantilla)"
  - "[!if] (directiva de plantilla)"
  - "[!loop] (directiva de plantilla)"
  - "[!output] (directiva de plantilla)"
  - "asistentes personalizados, directivas de plantilla"
  - "directivas, directivas de plantilla"
  - "directiva else ([!else])"
  - "directiva endif ([!endif])"
  - "directiva endloop ([!endloop])"
  - "directiva if ([!if])"
  - "directiva loop ([!loop])"
  - "directiva output ([!output])"
  - "directivas de plantilla"
ms.assetid: b6204153-813a-423c-b044-e39c352cc5af
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Directivas de plantilla
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las siguientes directivas de plantilla pueden utilizarse para personalizar el asistente tanto en un [archivo de plantilla](../ide/template-files.md) del asistente como en el propio [archivo Templates.inf](../ide/templates-inf-file.md).  
  
|Directiva|Descripción|  
|---------------|-----------------|  
|\[\!  if \]|Inicia una estructura de control que comprueba una condición.|  
|\[\!  else \]|Parte de la estructura de control \[\!  if \].  Comprueba otra condición.|  
|\[\!  endif \]|Termina la definición de una estructura de control \[\!  if \].|  
|\[\!  output \]|Puede utilizarse de estas dos formas:<br /><br /> -   \[\!  output "cadena" \] \(proporciona la cadena\).<br />-   \[\!  output SYMBOL\_STRING \] \(proporciona el valor del símbolo SYMBOL\_STRING\).|  
|\[\!  loop \]|Puede utilizarse de estas dos formas:<br /><br /> -   \[\!  loop \= 5 \]<br />-   \[\!  loop \= *NÚMERO\_DE\_PÁGINAS* \] \(donde *NÚMERO\_DE\_PÁGINAS* es un símbolo con un valor numérico\).|  
|\[\!  endloop \]|Termina una estructura de bucle.|  
  
 El corchete izquierdo \(\[\) seguido inmediatamente por un signo de admiración \(\!\) indica el principio de una directiva de plantilla.  El corchete derecho indica el final de una directiva de plantilla.  Ésta es la sintaxis necesaria:  
  
```  
[!directive params]  
```  
  
 Sólo se requiere un espacio o un carácter de no identificador entre *directiva* y *params*.  
  
## Ejemplo  
  
```  
[!if SAMPLE_RADIO_OPTION1]  
You have checked the option 'Sample radio button option 1'  
[!else]  
You have checked the option 'Sample radio button option 2'  
[!endif]  
```  
  
 En un archivo de plantilla, pueden utilizarse los siguientes operadores con las directivas anteriores:  
  
```  
+  
-     
=  
!=     
==     
||     
&&    
!  
```  
  
## Ejemplo  
  
```  
[!if SYMBOL_STRING != 0]  
```  
  
## Vea también  
 [Archivos creados para un asistente](../ide/files-created-for-your-wizard.md)   
 [asistente personalizado](../ide/custom-wizard.md)   
 [Crear un asistente personalizado](../ide/creating-a-custom-wizard.md)   
 [Diseñar un asistente](../ide/designing-a-wizard.md)