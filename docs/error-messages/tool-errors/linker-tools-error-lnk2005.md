---
title: "Error de las herramientas del vinculador LNK2005 | Microsoft Docs"
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
  - "LNK2005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2005"
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK2005
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

símbolo ya definido en objeto  
  
 El `symbol` proporcionado, que se muestra en su forma representativa, se definió varias veces.  
  
 Para más información, consulte los artículos de Knowledge Base:  
  
-   “Errores LNK2005 cuando las bibliotecas de vínculos en tiempo de ejecución de C se vinculan antes que las bibliotecas MFC” \(Q148652\)  
  
-   “Un operador delete sobrecargado globalmente provoca LNK2005” \(Q140440\)  
  
-   "Errores LNK2005 en new y delete al definir \_ATL\_MIN\_CRT" \(Q184235\).  
  
 Encontrará artículos de Knowledge Base en el CD\-ROM de MSDN Library o en [http:\/\/support.microsoft.com\/search](http://support.microsoft.com/search).  
  
 A este error le sigue el error irrecuperable [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md).  
  
### Posibles causas del error:  
  
1.  Mezclar bibliotecas estáticas y dinámicas y, al mismo tiempo, usar [\/clr](../../build/reference/clr-common-language-runtime-compilation.md).  
  
2.  El símbolo es una función empaquetada \(creada al compilar con [\/Gy](../../build/reference/gy-enable-function-level-linking.md)\) y se incluyó en varios archivos pero se cambió de una compilación a otra.  Recompilar todos los archivos que incluyen `symbol`.  
  
3.  El símbolo está definido de manera distinta en dos objetos miembros de diferentes bibliotecas, y se utilizaron los dos objetos miembros.  
  
4.  Hay un valor absoluto definido dos veces, con un valor distinto en cada definición.  
  
5.  Un archivo de encabezado declaró y definió una variable.  Entre las posibles soluciones están:  
  
    -   Declarar la variable en .h: `extern BOOL MyBool;` y, luego, asignarle en un archivo .c o .cpp: `BOOL MyBool = FALSE;`.  
  
    -   Declarar la variable [static](../../misc/static-cpp.md).  
  
    -   Declarar la variable [selectany](../../cpp/selectany.md).  
  
6.  Si usa uuid.lib combinado con otros archivos .lib que definen GUID \(por ejemplo, oledb.lib y adsiid.lib\).  Por ejemplo:  
  
    ```  
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject  
    already defined in uuid.lib(go7.obj)  
    ```  
  
     Para corregirlo, agregue [\/FORCE:MULTIPLE](../../build/reference/force-force-file-output.md) a las opciones de la línea de comandos del enlazador y compruebe que uuid.lib es la primera biblioteca a la que se hace referencia.