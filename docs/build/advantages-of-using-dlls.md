---
title: "Ventajas de utilizar archivos DLL | Microsoft Docs"
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
  - "DLL [C++], ventajas"
  - "vinculación dinámica [C++]"
  - "vinculación de carga dinámica [C++]"
  - "vincular [C++], dinámica y estática"
  - "vínculos [C++], dinámica y estática"
ms.assetid: 8956c8ee-e7b3-446f-a0c6-462381747690
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Ventajas de utilizar archivos DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La vinculación dinámica ofrece las siguientes ventajas:  
  
-   Ahorra memoria y reduce el intercambio de páginas.  Muchos procesos pueden utilizar simultáneamente un mismo archivo DLL, compartiendo una sola copia del mismo en la memoria.  En cambio, Windows debe cargar en la memoria una copia del código de la biblioteca para cada aplicación compilada con una biblioteca de vínculos estáticos.  
  
-   Ahorra espacio en disco.  Varias aplicaciones pueden compartir una única copia del archivo DLL en disco.  En cambio, las aplicaciones compiladas con una biblioteca de vínculos estáticos tienen el código de biblioteca vinculado en la imagen del ejecutable como una copia independiente.  
  
-   Es más fácil actualizar archivos DLL.  Cuando cambien las funciones de un archivo DLL, no será necesario volver a compilar y vincular las aplicaciones que las utilizan si no cambian los argumentos de la función y los valores devueltos.  En cambio, el código de un objeto vinculado estáticamente requiere que se vuelva a vincular la aplicación cuando cambien las funciones.  
  
-   Permite la asistencia post\-venta.  Por ejemplo, se puede modificar un archivo DLL de un controlador de vídeo de forma que permita una presentación que no estaba disponible en la versión comercial.  
  
-   Admite programas multilenguaje.  Programas creados con distintos lenguajes de programación pueden llamar a la misma función DLL siempre que sigan la convención de llamada a la función.  Los programas y la función DLL deben coincidir en los siguientes aspectos: el orden de inserción de los argumentos de la función en la pila, si la función o la aplicación es responsable de limpiar la pila y si se pasan argumentos en registros.  
  
-   Proporciona un mecanismo para extender las clases de biblioteca MFC.  Puede derivar clases a partir de las clases MFC existentes y colocarlas en un archivo DLL de extensión de MFC para que las utilicen las aplicaciones MFC.  
  
-   Facilita la creación de versiones internacionales.  Al colocar los recursos en un archivo DLL, es mucho más fácil crear versiones internacionales de una aplicación.  Puede colocar las cadenas de cada una de las versiones de lenguaje de la aplicación en un archivo DLL de recursos independiente y hacer que las distintas versiones de lenguaje carguen los recursos apropiados.  
  
 Una posible desventaja de utilizar archivos DLL es que la aplicación no es independiente; depende de la existencia de un módulo de archivo DLL separado.  
  
## ¿Qué desea hacer?  
  
-   [Exportar de un archivo DLL](../build/exporting-from-a-dll.md)  
  
-   [Vincular un ejecutable a un archivo DLL](../build/linking-an-executable-to-a-dll.md)  
  
-   [Inicializar un archivo DLL](../build/initializing-a-dll.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Archivos DLL que no están basados en MFC: información general](../build/non-mfc-dlls-overview.md)  
  
-   [Archivos DLL estándar vinculados estáticamente a MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Archivos DLL estándar vinculados dinámicamente a MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Archivos DLL de extensión: información general](../build/extension-dlls-overview.md)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)