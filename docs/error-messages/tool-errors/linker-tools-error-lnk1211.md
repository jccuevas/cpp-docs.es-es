---
title: "Error de las herramientas del vinculador LNK1211 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1211"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1211"
ms.assetid: 607400eb-4180-4892-817f-eedfa628af61
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK1211
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se encontró información de tipo precompilado; 'nombredearchivo' no vinculado o reemplazado  
  
 El archivo objeto dado, compilado con [\/Yc](../../build/reference/yc-create-precompiled-header-file.md), no se especificó en el comando LINK o se sobrescribió.  
  
 Si se está creando una biblioteca de depuración que utiliza encabezados precompilados y se especifica \/Yc y [\/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), Visual C\+\+ genera un archivo objeto precompilado que contiene información de depuración CodeView.  Este error se produce sólo cuando se almacena el archivo objeto precompilado en una biblioteca, se utiliza ésta para compilar una imagen ejecutable y los archivos objeto a que se hace referencia no contienen referencias transitivas a ninguna de las funciones que define el archivo objeto precompilado.  
  
 Existen dos métodos para resolver esta situación:  
  
-   Especifique la opción del compilador [\/Yd](../../build/reference/yd-place-debug-information-in-object-file.md) para agregar la información CodeView del encabezado precompilado a cada módulo de objeto.  Este método es menos deseable, ya que genera normalmente grandes módulos de objeto que pueden aumentar el tiempo requerido para vincular la aplicación.  
  
-   Especifique [\/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) y pase el nombre de cualquier cadena arbitraria al crear un archivo de encabezado precompilado que no contiene definiciones de función.  Esto indica al compilador que cree un símbolo en el archivo de encabezado precompilado y emita una referencia a ese símbolo en cada uno de los archivos objeto que utilizan el archivo de encabezado precompilado asociado al archivo objeto precompilado.  
  
 Cuando se compila un módulo con **\/Yc** e **\/Yl**, el compilador crea un símbolo similar a `__@@_PchSym_@00@...@symbol_name`, donde los puntos suspensivos \(...\) representan una cadena de caracteres generada por el compilador, y lo almacena en el módulo de objetos.  Cualquier archivo de código fuente que se compile con este encabezado precompilado hace referencia al símbolo especificado, a causa de lo cual el vinculador incluye el módulo de objetos y su información de depuración desde la biblioteca.  
  
 Para obtener más información acerca de este error, vea el artículo Q102697 de Knowledge Base PRB: Build Errors Using Precompiled Header in Debugging Lib.