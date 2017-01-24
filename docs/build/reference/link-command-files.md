---
title: "Archivos de comandos de LINK | Microsoft Docs"
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
  - "link"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos de comandos [C++]"
  - "archivos de comandos [C++], LINK"
  - "LINK (herramienta) [C++]"
  - "LINK (herramienta) [C++], sintaxis de línea de comandos"
  - "sintaxis, LINK (archivos de comandos)"
  - "archivos de texto, pasar argumentos a LINK"
ms.assetid: 7154511c-32b9-4e5b-a515-3922fa9de48e
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Archivos de comandos de LINK
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Es posible pasar argumentos de línea de comandos a LINK como archivos de comandos.  Para especificarle un archivo de comandos al vinculador, utilice la siguiente sintaxis:  
  
```  
LINK @commandfile  
```  
  
 `commandfile`es el nombre de un archivo de texto.  No se permiten espacios o tabuladores entre el signo arroba \(@\) y el nombre de archivo.  No hay ninguna extensión predeterminada: es necesario especificar el nombre completo del archivo, con la extensión incluida.  No se pueden utilizar comodines.  Con el nombre de archivo, se puede especificar una ruta absoluta o relativa.  LINK no utiliza una variable de entorno para buscar el archivo.  
  
 En el archivo de comandos, es posible separar los argumentos con espacios o tabulaciones, como en la línea de comandos, o con caracteres de nueva línea.  
  
 En un archivo de comandos se puede especificar una parte o la totalidad de la línea de comandos.  En el comando de LINK se pueden utilizar varios archivos de comandos.  LINK acepta la entrada del archivo de comandos como si estuviera especificada en esa ubicación de la línea de comandos.  No se permite utilizar archivos de comandos anidados.  A menos que se utilice la opción [\/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md), LINK repetirá el contenido de los archivos de comandos.  
  
## Ejemplo  
 El siguiente comando, de compilación de una DLL, pasa en archivos de comandos diferentes los nombres de los archivos de objetos y las bibliotecas y usa un tercer archivo de comandos para especificar la opción \/EXPORTS:  
  
```  
link /dll @objlist.txt @liblist.txt @exports.txt  
```  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)