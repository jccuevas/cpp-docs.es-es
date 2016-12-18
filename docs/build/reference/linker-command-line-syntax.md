---
title: "Sintaxis de la l&#237;nea de comandos del vinculador | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LINK (herramienta) [C++], sintaxis de línea de comandos"
  - "vinculador [C++], sintaxis"
  - "línea de comandos del vinculador [C++]"
ms.assetid: e2a31e17-77bd-4e74-9305-75b105b26539
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Sintaxis de la l&#237;nea de comandos del vinculador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilice la siguiente sintaxis de comandos para ejecutar LINK.EXE:  
  
```  
LINK arguments  
```  
  
 `arguments` incluye opciones y nombres de archivo que pueden especificarse en cualquier orden.  Las opciones se procesan en primer lugar, seguidas de los archivos.  Separe los argumentos con uno o varios espacios o tabulaciones.  
  
> [!NOTE]
>  Sólo puede iniciar esta herramienta desde el símbolo del sistema de [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)].  No puede iniciar desde una ventana del símbolo del sistema o desde el Explorador de archivos.  
  
 En la línea de comandos, las opciones están formadas por un especificador de opción, que puede ser un guión \(–\) o una barra diagonal \(\/\), seguido por el nombre de la opción.  Los nombres de opción no pueden abreviarse.  Algunas opciones utilizan un argumento, que deberá ir precedido por dos puntos \(:\).  Salvo que se incluyan en el interior de una cadena entrecomillada en la opción \/COMMENT, no se permiten espacios o tabulaciones en la especificación de las opciones.  Especifique los argumentos numéricos en notación decimal o de lenguaje C.  En los nombres de opción y sus argumentos de palabra clave y nombre de archivo, no se distingue entre mayúsculas y minúsculas, algo que sí ocurre en los identificadores usados como argumentos.  
  
 Para pasar un archivo al vinculador, deberá especificarse su nombre en la línea de comandos después del comando de LINK.  Con el nombre de archivo, puede especificarse una ruta de acceso absoluta o relativa, así como utilizar comodines.  Si se invalida el punto \(.\) y la extensión del archivo, LINK, para buscar el archivo, supondrá que su extensión es .obj.  LINK no usa las extensiones de los nombres de archivo o su omisión para realizar suposiciones sobre el contenido de los archivos; determina el tipo del archivo examinándolo y, después, lo procesa en consecuencia.  
  
 link.exe devuelve cero si no se produce ningún error.  De lo contrario, devuelve el número de error que detuvo el vínculo.  Por ejemplo, si el vinculador genera LNK1104, el vinculador devuelve 1104.  En consecuencia, el número de error inferior devuelto en un error por el vinculador es 1000.  Un valor devuelto de 128 representa un problema de configuración con el sistema operativo o un archivo .config; el cargador no se cargó link.exe o c2.dll.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)