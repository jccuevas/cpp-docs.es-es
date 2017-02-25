---
title: "/BASE (Direcci&#243;n base) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/base"
  - "VC.Project.VCLinkerTool.BaseAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/BASE (opción del vinculador)"
  - "@ (símbolo para dirección base)"
  - "en el símbolo de signo para la dirección base"
  - "direcciones base [C++]"
  - "BASE (opción del vinculador)"
  - "-BASE (opción del vinculador)"
  - "DLL [C++], vincular"
  - "variables de entorno [C++], LIB"
  - "archivos ejecutables [C++], dirección base"
  - "tamaño de dirección clave"
  - "LIB (variable de entorno)"
  - "programas [C++], dirección base"
  - "programas [C++], impedir la reubicación"
  - "punto y coma [C++], especificador"
ms.assetid: 00b9f6fe-0bd2-4772-a69c-7365eb199069
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /BASE (Direcci&#243;n base)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/BASE:{address[,size] | @filename,key}  
```  
  
 La opción \/BASE establece una dirección base para el programa, con lo que se reemplaza la ubicación predeterminada de los archivos .exe \(0x400000\) o DLL \(0x10000000\).  En primer lugar, el sistema operativo intenta cargar los programas en la dirección base especificada o predeterminada.  Si en ella no hay espacio suficiente, el sistema cambiará la ubicación del programa.  Para evitarlo, se deberá utilizar la opción [\/FIXED](../../build/reference/fixed-fixed-base-address.md).  
  
 Si *address* no es un múltiplo de 64K, el vinculador generará un error.  Opcionalmente, puede especificar el tamaño del programa, de modo que el vinculador le advierta si el programa no puede ajustarse al tamaño especificado.  
  
 En la línea de comandos, otro método para especificar la dirección base consiste en usar *filename* precedido del signo arroba \(@\) e incluir `key` en el archivo.  *filename* es un archivo de texto que contiene la ubicación y el tamaño de todas las DLL que va a usar el programa.  El vinculador busca *filename* en la ruta de acceso especificada o, de no especificarse, en los directorios mencionados en la variable de entorno LIB.  Cada línea de *filename* representa una DLL y tiene la siguiente sintaxis:  
  
```  
  
key address [size] ;comment  
```  
  
 El parámetro `key` está formado por una cadena de caracteres alfanuméricos sin distinción entre mayúsculas y minúsculas.  Normalmente, aunque no de forma obligatoria, es el nombre de una DLL.  El parámetro `key` va seguido de una dirección base \(*address*\) en lenguaje C, con notación decimal o hexadecimal, y de un tamaño máximo opcional \(`size`\).  Los tres argumentos van separados por espacios o tabulaciones.  El vinculador mostrará una advertencia si el tamaño especificado \(`size`\) es inferior al espacio virtual de direcciones requerido por el programa.  `comment` se especifica con un punto y coma \(;\) y puede estar en esa misma línea o en una línea aparte.  El vinculador omitirá cualquier texto situado entre el punto y coma y el final de la línea.  En este ejemplo se muestra parte de un archivo como el mencionado:  
  
```  
main   0x00010000    0x08000000    ; for PROJECT.exe  
one    0x28000000    0x00100000    ; for DLLONE.DLL  
two    0x28100000    0x00300000    ; for DLLTWO.DLL  
```  
  
 Si el archivo que contiene estas líneas se denomina DLLS.txt, el comando del ejemplo siguiente aplicará esta información:  
  
```  
link dlltwo.obj /dll /base:@dlls.txt,two  
```  
  
## Comentarios  
 Es posible reducir la paginación y mejorar el rendimiento de un programa asignando direcciones base para evitar que las DLL se superpongan en el espacio de direcciones.  
  
 Otra forma de establecer la dirección base es por medio del argumento *BASE* en una instrucción [NAME](../../build/reference/name-c-cpp.md) o [LIBRARY](../../build/reference/library.md).  Las opciones \/BASE y [\/DLL](../../build/reference/dll-build-a-dll.md) juntas equivalen a la instrucción **LIBRARY**.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Avanzadas**.  
  
4.  Modifique la propiedad **Dirección base**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)