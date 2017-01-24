---
title: "/ORDER (Colocar las funciones en orden) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.FunctionOrder"
  - "/order"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ORDER (opción del vinculador)"
  - "LINK (herramienta) [C++], optimización de programas"
  - "LINK (herramienta) [C++], ajuste del intercambio"
  - "ORDER (opción del vinculador)"
  - "-ORDER (opción del vinculador)"
  - "paginación, optimizar"
ms.assetid: ecf5eb3e-e404-4e86-9a91-4e5ec157261a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ORDER (Colocar las funciones en orden)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ORDER:@filename  
```  
  
## Parámetros  
 *filename*  
 Archivo de texto que especifica el orden de vinculación de las funciones COMDAT.  
  
## Comentarios  
 La opción \/ORDER indica a LINK que optimice el programa mediante la colocación de determinados COMDAT dentro de la imagen en un orden predeterminado.  LINK coloca las funciones en el orden especificado en cada una de las secciones de la imagen.  
  
 El orden deberá especificarse en *filename*, archivo de texto \(archivo de respuesta\) en el que se enumeran las COMDAT de la vinculación en el orden deseado.  Cada línea de *filename* deberá contener el nombre de una COMDAT.  Los objetos compilados con la opción \/Gy contendrán funciones COMDAT.  Los nombres de función distinguen entre mayúsculas y minúsculas.  
  
 LINK usa formatos representativos para los identificadores.  El compilador decora los identificadores cuando crea el archivo .obj.  La herramienta [DUMPBIN](../../build/reference/dumpbin-reference.md) se utiliza para obtener el formato representativo de un identificador que necesite especificarse en el vinculador.  Para obtener más información acerca de los nombres representativos, vea [Nombres representativos](../../build/reference/decorated-names.md).  
  
 Si se usa más de una especificación \/ORDER, la última especificada será la que tenga efecto.  
  
 El orden de vinculación permite optimizar el comportamiento de paginación de un programa con un ajuste del intercambio: agrupando cada función con las funciones a las que llama.  También es posible agrupar las funciones a las que se llame con más frecuencia.  Estas técnicas aumentan la probabilidad de que la función a la que se llama se encuentre en la memoria cuando se necesite, por lo que no deberá ser paginada desde el disco.  
  
 El vinculador antepondrá un carácter de subrayado \(\_\) a todos los nombres representativos de *filename* que no empiecen con un signo de interrogación \(?\) o una arroba \(@\).  Por ejemplo, si un archivo objeto contiene `extern "C" int func(int)` e `int main(void)`, DUMPBIN [\/SYMBOLS](../../build/reference/symbols.md) mostrará los siguientes nombres representativos:  
  
```  
009 00000000 SECT3  notype ()    External     | _func  
00A 00000008 SECT3  notype ()    External     | _main  
```  
  
 No obstante, los nombres que deberán especificarse en el archivo de orden son `func` y `main`.  
  
 La opción \/ORDER deshabilita la vinculación incremental.  
  
> [!NOTE]
>  LINK no puede ordenar las funciones estáticas porque sus nombres no son nombres de símbolo públicos.  Si se especifica \/ORDER, se generará la advertencia del vinculador LNK4037 para cada símbolo que, en el archivo de orden, sea estático o no pueda encontrarse.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, vea [Establecer las propiedades de un proyecto de Visual C\+\+](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **Vinculador**.  
  
3.  Haga clic en la página de propiedades **Optimización**.  
  
4.  Modifique la propiedad **Orden de funciones**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.FunctionOrder%2A>.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)