---
title: "/MANIFESTUAC (Incrustar informaci&#243;n de UAC en el manifiesto) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.UACUIAccess"
  - "VC.Project.VCLinkerTool.UACExecutionLevel"
  - "VC.Project.VCLinkerTool.EnableUAC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MANIFESTUAC (opción del vinculador)"
  - "MANIFESTUAC (opción del vinculador)"
  - "-MANIFESTUAC (opción del vinculador)"
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /MANIFESTUAC (Incrustar informaci&#243;n de UAC en el manifiesto)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica si la información de Control de cuentas de usuario \(UAC\) debe incrustarse en el manifiesto del programa.  
  
## Sintaxis  
  
```  
/MANIFESTUAC  
/MANIFESTUAC:NO  
/MANIFESTUAC:fragment  
/MANIFESTUAC:level=_level  
/MANIFESTUAC:uiAccess=_uiAccess  
```  
  
#### Parámetros  
 `fragment`  
 Una cadena que contiene los valores de `level` y `uiAccess`.  Para obtener más información, vea la sección Comentarios más adelante en este tema.  
  
 `_level`  
 Uno de los siguientes: *asInvoker* *highestAvailable* o *requireAdministrator*.  El valor predeterminado es asInvoker.  Para obtener más información, vea la sección Comentarios más adelante en este tema.  
  
 `_uiAccess`  
 `true` si desea que la aplicación omita los niveles de protección de la interfaz de usuario y dirija las entradas de datos a ventanas con un nivel de permisos superior en el escritorio; de lo contrario, `false`.  Tiene como valor predeterminado `false`.  Establézcalo en `true` solo para aplicaciones relacionadas con la accesibilidad de la interfaz de usuario.  
  
## Comentarios  
 Si especifica varias opciones \/MANIFESTUAC en la línea de comandos, tendrá prioridad la última que escriba.  
  
 Las opciones de \/MANIFESTUAC:level son las siguientes:  
  
-   `asInvoker`: la aplicación se ejecutará con los mismos permisos que el proceso que la inició.  La aplicación se puede elevar a un nivel de permisos superior seleccionando **Ejecutar como administrador**.  
  
-   highestAvailable: la aplicación se ejecutará con el máximo nivel de permisos posible.  Si el usuario que inicia la aplicación es miembro del grupo Administradores, esta opción es igual que requireAdministrator.  Si el máximo nivel de permisos disponible es superior al nivel del proceso de apertura, el sistema solicitará las credenciales.  
  
-   requireAdministrator: la aplicación se ejecutará con permisos de administrador.  El usuario que inicia la aplicación debe ser miembro del grupo Administradores.  Si el proceso de apertura no se está ejecutando con permisos administrativos, el sistema solicitará las credenciales.  
  
 El nivel y los valores de uiAccess se pueden especificar en un solo paso mediante la opción \/MANIFESTUAC:fragmento.  El fragmento deben tener el formato siguiente:  
  
```  
"level=[ asInvoker | highestAvailable | requireAdministrator ] uiAccess=[ true | false ]"  
```  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Expanda el nodo **Propiedades de configuración**.  
  
3.  Expanda el nodo **Vinculador**.  
  
4.  Seleccione la página de propiedades **Archivo de manifiesto**.  
  
5.  Modifique las propiedades **Habilitar Control de cuentas de usuario \(UAC\)**, **Nivel de ejecución de UAC** y **Omitir protección de IU de UAC**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)