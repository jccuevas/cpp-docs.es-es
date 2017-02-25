---
title: "/SECTION (Especificar los atributos de la secci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/section"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/SECTION (opción del vinculador)"
  - "atributos de sección"
  - "SECTION (opción del vinculador)"
  - "-SECTION (opción del vinculador)"
ms.assetid: 92b69d81-e421-462e-b46f-7d0dff9b9d16
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /SECTION (Especificar los atributos de la secci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/SECTION:name,[[!]{DEKPRSW}][,ALIGN=#]  
```  
  
## Comentarios  
 La opción \/SECTION cambia los atributos de una sección mediante la invalidación de los atributos establecidos al compilarse el archivo .obj para la sección.  
  
 Una sección de un archivo portable ejecutable \(PE\) es el equivalente aproximado de un segmento o de los recursos de un archivo ejecutable nuevo \(NE\).  Las secciones contienen o código o datos.  A diferencia de los segmentos, las secciones son bloques de memoria contigua sin restricciones de tamaño.  Algunas secciones contienen código o datos que el programa declara y utiliza directamente, mientras que otras, denominadas secciones de datos y creadas por el vinculador y el administrador de bibliotecas \(lib.exe\), contienen información vital para el sistema operativo.  Para obtener más información sobre los archivos NE, consulte el artículo de Knowledge Base "Executable\-File Header Format" \(Q65122\).  Encontrará artículos de Knowledge Base en MSDN Library, o en [http:\/\/support.microsoft.com](http://support.microsoft.com).  
  
 Escriba el signo de dos puntos \(:\) y el nombre \(*name*\) de la sección.  En *name* se hará distinción entre mayúsculas y minúsculas.  
  
 No se podrán utilizar los nombres siguientes, pues causarían conflictos con los nombres estándar.  Por ejemplo, .sdata se utiliza en las plataformas RISC:  
  
-   .arch  
  
-   .bss  
  
-   .data  
  
-   .edata  
  
-   .idata  
  
-   .pdata  
  
-   .rdata  
  
-   .reloc  
  
-   .rsrc  
  
-   .sbss  
  
-   .sdata  
  
-   .srdata  
  
-   .text  
  
-   .xdata  
  
 Es posible especificar uno o varios atributos para la sección.  En estos atributos, mostrados a continuación, no se distingue entre mayúsculas y minúsculas.  Es necesario especificar todos los atributos que deba contener la sección; la omisión de algún carácter causará la desactivación del bit del atributo.  Si no se especifica R, W o E, el estado de lectura, escritura o ejecución existente permanecerá inalterado.  
  
 Para negar un atributo, su carácter deberá ir precedido por un signo de admiración \(\!\).  A continuación se explica el significado de los caracteres de atributo.  
  
|Carácter|Atributo|Significado|  
|--------------|--------------|-----------------|  
|E|Ejecutar|La sección es ejecutable|  
|R|Leer|Permite operaciones de lectura en los datos|  
|W|Escritura|Permite operaciones de escritura en los datos|  
|S|Shared|Comparte la sección entre todos los procesos que cargan la imagen|  
|D|Discardable|Marca la sección como descartable|  
|K|Cacheable|Marca la sección como no válida para almacenarse en caché|  
|P|Pageable|Marca la sección como no paginable|  
  
 K y P tienen una peculiaridad: los marcadores de sección que les corresponden tienen un sentido negativo.  Si se especifica uno de ellos en la sección .text \(\/SECTION:.text,K\), no existirá diferencia en los marcadores de sección al ejecutar [DUMPBIN](../../build/reference/dumpbin-options.md) con la opción [\/HEADERS](../../build/reference/headers.md), pues ya estaba en caché de forma implícita.  Para quitar el valor predeterminado, se deberá especificar \/SECTION:.text,\!K, con lo que DUMPBIN revelará todas las características de la sección, incluyendo "no almacenada en caché".  
  
 Una sección en el archivo PE que no tenga establecido E, R o W probablemente no será válida.  
  
 ALIGN*\=\#* permite especificar un valor de alineación para una sección concreta.  Para obtener más información, vea [\/ALIGN](../../build/reference/align-section-alignment.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Línea de comandos**.  
  
4.  Escriba la opción en el cuadro **Opciones adicionales**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)