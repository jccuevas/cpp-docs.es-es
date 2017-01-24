---
title: "/CLRTHREADATTRIBUTE (Establecer el atributo de subproceso de CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.CLRThreadAttribute"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CLRTHREADATTRIBUTE (opción del vinculador)"
  - "-CLRTHREADATTRIBUTE (opción del vinculador)"
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /CLRTHREADATTRIBUTE (Establecer el atributo de subproceso de CLR)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifique explícitamente el atributo de subprocesamiento del punto de entrada del programa CLR.  
  
## Sintaxis  
  
```  
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}  
```  
  
#### Parámetros  
 MTA  
 Aplica el atributo MTAThreadAttribute al punto de entrada del programa.  
  
 \(Ninguno\)  
 Equivale a no especificar \/CLRTHREADATTRIBUTE.  Permite que Common Language Runtime \(CLR\) establezca el atributo de subprocesamiento predeterminado.  
  
 STA  
 Aplica el atributo STAThreadAttribute al punto de entrada del programa.  
  
## Comentarios  
 El establecimiento del atributo de subproceso solo es posible cuando se compila un .exe, ya que afecta al punto de entrada del subproceso principal.  
  
 Si utiliza el punto de entrada predeterminado \(main o wmain, por ejemplo\), especifique el modelo de subprocesos mediante \/CLRTHREADATTRIBUTE o colocando el atributo de subprocesamiento \(STAThreadAttribute o MTAThreadAttribute\) en la función de entrada predeterminada.  
  
 Si utiliza un punto de entrada que no es el predeterminado, especifique el modelo de subprocesos mediante \/CLRTHREADATTRIBUTE o colocando el atributo de subprocesamiento en la función de entrada no predeterminada y, a continuación, especifique el punto de entrada no predeterminado con [\/ENTRY](../../build/reference/entry-entry-point-symbol.md).  
  
 Si el modelo de subprocesos especificado en el código fuente no es conforme con el especificado con \/CLRTHREADATTRIBUTE, el vinculador omite \/CLRTHREADATTRIBUTE y aplica el modelo de subprocesos especificado en código fuente.  
  
 Será necesario que utilice el subprocesamiento único, por ejemplo, si su programa de CLR hospeda un objeto COM que utiliza subprocesamiento único.  Si el programa de CLR utiliza subprocesamiento múltiple, no puede hospedar un objeto COM que utilice subprocesamiento único.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **Vinculador**.  
  
4.  Seleccione la página de propiedades **Avanzadas**.  
  
5.  Modifique la propiedad **Atributo de subproceso de CLR**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)