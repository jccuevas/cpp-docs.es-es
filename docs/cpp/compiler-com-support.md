---
title: "Compatibilidad con COM del compilador | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe (compilador), compatibilidad con COM"
  - "COM, compatibilidad del compilador"
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Compatibilidad con COM del compilador
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 El compilador de Visual C\+\+ puede leer directamente bibliotecas de tipos de modelo de objetos componentes \(COM\) y traducir el contenido a código fuente de C\+\+ que se puede incluir en la compilación.  Existen extensiones de lenguaje disponibles para facilitar la programación COM en el cliente.  
  
 Mediante el uso de la [directiva de preprocesador \#import](../preprocessor/hash-import-directive-cpp.md), el compilador puede leer una biblioteca de tipos y convertirla en un archivo de encabezado de C\+\+ que describe las interfaces COM como clases.  Existe un conjunto de atributos `#import` disponible para el control por parte del usuario del contenido de los archivos de encabezado de biblioteca de tipos resultantes.  
  
 Puede utilizar el [uuid](../cpp/uuid-cpp.md) de atributo extendido [\_\_declspec](../cpp/declspec.md) para asignar un identificador único global \(GUID\) a un objeto COM.  Se puede usar la palabra clave [\_\_uuidof](../cpp/uuidof-operator.md) para extraer el GUID asociado a un objeto COM.  Se puede usar otro atributo `__declspec`, [property](../cpp/property-cpp.md), para especificar los métodos **get** y **set** para un miembro de datos de un objeto COM.  
  
 Se proporciona un conjunto de funciones globales de compatibilidad con COM para admitir los tipos **VARIANT** y `BSTR`, implementar punteros inteligentes y encapsular el objeto de error iniciado por `_com_raise_error`:  
  
-   [Funciones globales COM de compilador](../cpp/compiler-com-global-functions.md)  
  
-   [\_bstr\_t](../cpp/bstr-t-class.md)  
  
-   [\_com\_error](../cpp/com-error-class.md)  
  
-   [\_com\_ptr\_t](../cpp/com-ptr-t-class.md)  
  
-   [\_variant\_t](../cpp/variant-t-class.md)  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Clases de compatibilidad con COM del compilador](../cpp/compiler-com-support-classes.md)   
 [Funciones globales COM del compilador](../cpp/compiler-com-global-functions.md)