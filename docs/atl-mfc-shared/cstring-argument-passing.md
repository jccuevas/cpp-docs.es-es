---
title: "CString Argument Passing | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "argument passing [C++]"
  - "argument passing [C++], C strings"
  - "arguments [C++], pasar"
  - "CString objects, pasar argumentos"
  - "funciones [C++], strings as input/output"
  - "pasar argumentos, C strings"
  - "string arguments"
  - "cadenas [C++], as function input/output"
ms.assetid: a67bebff-edf1-4cf4-bbff-d1cc6a901099
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CString Argument Passing
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo pasar los objetos de [CString](../atl-mfc-shared/reference/cstringt-class.md) a funciones y cómo devolver los objetos de `CString` de funciones.  
  
##  <a name="_core_cstring_argument.2d.passing_conventions"></a> Convenciones Argumento\-Que Pasan CString  
 Cuando se define una interfaz de clase, debe determinar la convención argumento\-que pasa para las funciones miembro.  Hay algunas reglas estándar para pasar y devolver los objetos de `CString` .  Si sigue las reglas descritas en [cadenas como entradas de la función](#_core_strings_as_function_inputs) y [Cadenas como resultados de la función](#_core_strings_as_function_outputs), tendrá un código eficaz, correcto.  
  
##  <a name="_core_strings_as_function_inputs"></a> cadenas como entradas de la función  
 La manera más eficaz y más seguro utilizar un objeto de `CString` a las funciones llamadas es pasar un objeto de `CString` a la función.  A pesar del nombre, un objeto de `CString` no almacena una cadena internamente como c. la cadena de estilo que tiene un carácter null final.  En su lugar, un objeto de `CString` conserva la pista cuidadosa del número de caracteres que tiene.  Teniendo `CString` proporcione un puntero de `LPCTSTR` a una cadena terminada en null es una pequeña cantidad de trabajo que puede resultar significativa si el código hacerlo constantemente.  El resultado es temporal porque cualquier cambio en el contenido de `CString` reemplaza las antiguas copias del puntero de `LPCTSTR` .  
  
 Tiene sentido de proporcionar en algunos casos una cadena de lenguaje c.  Por ejemplo, puede haber una situación donde una función denominada está escrita en C y no admite objetos.  En este caso, fuerce el parámetro de `CString` a `LPCTSTR`, y la función obtendrá c. cadena terminada en null de estilo.  También puede ir la dirección y crear un objeto de `CString` utilizando el constructor de `CString` que acepta c. parámetro de cadena de estilo.  
  
 Si fuese el contenido de la cadena a cambiar por una función, declare el parámetro como una referencia`CString` que no es una constante \(**CString&**\).  
  
##  <a name="_core_strings_as_function_outputs"></a> Cadenas como resultados de la función  
 Puede devolver normalmente los objetos de `CString` de funciones porque los objetos de `CString` siguen la semántica de valores como tipos primitivos.  para devolver una cadena de sólo lectura, utilice una referencia`CString` constante \(**const CString&**\).  El ejemplo siguiente se muestra el uso de los parámetros y los tipos de devolución de `CString` :  
  
 [!code-cpp[NVC_ATLMFC_Utilities#197](../atl-mfc-shared/codesnippet/CPP/cstring-argument-passing_1.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities#198](../atl-mfc-shared/codesnippet/CPP/cstring-argument-passing_2.cpp)]  
  
## Vea también  
 [Cadenas](../atl-mfc-shared/strings-atl-mfc.md)