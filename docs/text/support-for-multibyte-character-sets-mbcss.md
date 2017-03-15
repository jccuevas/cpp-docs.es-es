---
title: "Compatibilidad con los juegos de caracteres multibyte (MBCS) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mbcs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "juegos de caracteres [C++], multibyte"
  - "MBCS [C++]"
  - "MBCS [C++], acerca de MBCS"
  - "caracteres multibyte [C++]"
ms.assetid: b498733c-a1e1-45e3-8f26-d6da3cb5f2dd
caps.latest.revision: 11
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 11
---
# Compatibilidad con los juegos de caracteres multibyte (MBCS)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los juegos de caracteres multibyte \(MBCS\) son un enfoque anterior a la necesidad de admitir juegos de caracteres, como el japonés y el chino, que no pueden representarse en un solo byte.  Si está realizando nuevo desarrollo, debe utilizar Unicode para todas las cadenas de texto, excepto quizás las cadenas del sistema que los usuarios finales no ven.  MBCS es una tecnología heredada y no se recomienda para el nuevo desarrollo.  
  
 La implementación más habitual de MBCS son los juegos de caracteres de doble byte \(DBCS\).  Visual C\+\+ en general, y MFC en particular, están totalmente habilitados para DBCS.  
  
> [!WARNING]
>  En Visual Studio 2013 y versiones posteriores, las bibliotecas MFC para la codificación de caracteres multibyte \(MBCS\) se suministrarán como complemento a Visual Studio y estarán disponibles gratuitamente para los clientes de Visual Studio \(solo ediciones Professional y Enterprise\) en el sitio de descarga de MSDN.  
>   
>  Las bibliotecas requieren aproximadamente 440 MB en la unidad y la instalación incluye todas las versiones localizadas de las bibliotecas.  Puede instalarse en cualquier equipo en el que esté instalado Visual Studio Community Professional o Enterprise y que tenga habilitada la característica de MFC incorporada.  
>   
>  Si desinstala o repara Visual Studio, las bibliotecas de MBCS también se desinstalan o se reparan.  Sin embargo, si solo quita la característica de MFC, las bibliotecas de MBCS permanecerán en el sistema.  Si repara las bibliotecas de MBCS, Visual Studio no se modifica de ningún modo.  
>   
>  Los paquetes redistribuibles para Visual Studio 2013 y versiones posteriores se incluirán las DLL de MBCS para MFC.  No se necesita ningún paso adicional para redistribuir las DLL a los clientes.  
  
 Para obtener ejemplos, vea los archivos de código fuente de MFC.  
  
 Para las plataformas utilizadas en mercados cuyos idiomas utilizan juegos de caracteres de gran tamaño, la mejor alternativa a Unicode es MBCS.  MFC admite MBCS mediante el uso de tipos de datos internacionalizables y funciones en tiempo de ejecución de C.  Los programadores deben hacer lo mismo en su propio código.  
  
 En MBCS, los caracteres están codificados en uno o dos bytes.  En los caracteres de dos bytes, el primero, o byte inicial, indica que él mismo y el byte siguiente deben interpretarse como un solo carácter.  El primer byte procede de un intervalo de códigos reservado para su utilización como bytes iniciales.  Los intervalos de bytes que pueden ser bytes iniciales dependen de la página de códigos que se utiliza.  Por ejemplo, la página de códigos japonesa 932 utiliza el intervalo de 0x81 a 0x9F como bytes iniciales, pero la página de códigos coreana 949 utiliza un intervalo distinto.  
  
 Conviene tener en cuenta los siguientes aspectos en la programación con MBCS.  
  
 Caracteres MBCS en el entorno  
 Los caracteres MBCS pueden aparecer en cadenas como nombres de archivo y de directorio.  
  
 Operaciones de edición  
 Las operaciones de edición en aplicaciones MBCS se deben ejecutar en caracteres, no en bytes.  El símbolo de intercalación no debe dividir un carácter, la tecla de dirección DERECHA debe desplazar un carácter hacia la derecha, y así sucesivamente.  **Eliminar** debe eliminar un carácter. **Deshacer** debe volver a insertarlo.  
  
 Control de cadenas  
 En una aplicación que utiliza MBCS, el control de cadenas plantea problemas especiales.  Los caracteres de ambos anchos se mezclan en una sola cadena; por consiguiente, no se debe olvidar de que hay que comprobar los bytes iniciales.  
  
 Compatibilidad con bibliotecas en tiempo de ejecución  
 MFC y la biblioteca en tiempo de ejecución de C admiten la programación de un solo byte, MBCS y Unicode.  Las cadenas de un solo byte se procesan con la familia `str` de funciones en tiempo de ejecución, las cadenas MBCS se procesan con las funciones `_mbs` correspondientes, y las cadenas Unicode se procesan con las funciones *wcs* correspondientes.  Las implementaciones de funciones miembro de clase de MFC utilizan funciones en tiempo de ejecución portables, que se asignan bajo las circunstancias correctas a la familia `str` normal de funciones, las funciones MBCS o las funciones Unicode, como se describe en "Portabilidad de MBCS\/Unicode".  
  
 Portabilidad de MBCS\/Unicode  
 Si se utiliza el archivo de encabezado Tchar.h, se pueden compilar aplicaciones de un solo byte, MBCS y Unicode a partir de los mismos códigos fuente.  Tchar.h define macros que empiezan por *\_tcs*, que se asignan a las funciones `str`, `_mbs` o *wcs*, según proceda.  Para compilar MBCS, se ha de definir el símbolo **\_MBCS**.  Para compilar Unicode, se ha de definir el símbolo **\_UNICODE**.  De forma predeterminada, **\_MBCS** está definido para aplicaciones MFC.  Para obtener más información, vea [Asignaciones de texto genérico en Tchar.h](../Topic/Generic-Text%20Mappings%20in%20Tchar.h.md).  
  
> [!NOTE]
>  El comportamiento no se define si se definen conjuntamente **\_UNICODE** y **\_MBCS**.  
  
 Los archivos de encabezado Mbctype.h y Mbstring.h definen macros y funciones específicas de MBCS, que pueden ser necesarias en algunos casos.  Por ejemplo, `_ismbblead` indica si un determinado byte de una cadena es un byte inicial.  
  
 Con fines de portabilidad internacional, se debe codificar el programa con [Unicode](../text/support-for-unicode.md) o con los juegos de caracteres multibyte \(MBCS\).  
  
## ¿Qué desea hacer?  
  
-   [Habilitar MBCS en mi programa](../text/international-enabling.md)  
  
-   [Habilitar Unicode y MBCS en mi programa](../text/internationalization-strategies.md)  
  
-   [Utilizar MBCS para crear un programa internacionalizado](../Topic/MBCS%20Programming%20Tips.md)  
  
-   [Ver un resumen de programación con MBCS](../Topic/MBCS%20Programming%20Tips.md)  
  
-   [Obtener información sobre asignaciones de texto genérico para portabilidad de ancho de byte](../Topic/Generic-Text%20Mappings%20in%20Tchar.h.md)  
  
## Vea también  
 [Texto y cadenas](../text/text-and-strings-in-visual-cpp.md)   
 [Compatibilidad con MBCS en Visual C\+\+](../text/mbcs-support-in-visual-cpp.md)