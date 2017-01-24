---
title: "String Data Management | Microsoft Docs"
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
  - "Unicode, string objects"
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# String Data Management
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ proporciona varias maneras de administrar datos de cadena:  
  
-   [Manipulación de cadenas](../c-runtime-library/string-manipulation-crt.md) para trabajar con cadenas terminadas en null de estilo C  
  
-   La API Win32 funciona para administrar cadenas  
  
-   La clase [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md)de MFC, que proporciona objetos string flexibles, tamaño  
  
-   Ordenar [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md), que proporciona un objeto de cadena de la MFC\- independiente con la misma funcionalidad que `CString`  
  
 Casi todos los programas trabajan con datos de la cadena.  La clase de `CString` MFC es a menudo la mejor solución para administrar flexible de la cadena.  A partir de la versión 7,0, `CString` se puede utilizar en MFC o programas de la MFC\- independiente.  La biblioteca en tiempo de ejecución y `CString` admiten las cadenas que contienen caracteres \(anchos\) multibyte, como en Unicode o programación con MBCS.  
  
 En este artículo se describe los servicios de uso general que la biblioteca de clases proporciona relacionado para la manipulación de cadenas.  Temas cubiertos en incluyen de caso:  
  
-   [Unicode y MBCS proporcionan portabilidad](#_core_unicode_and_mbcs_provide_portability)  
  
-   [CStrings y const carbonizan punteros](#_core_cstrings_and_const_char_pointers)  
  
-   [Recuento de referencias de CString](#_core_cstring_reference_counting)  
  
 La clase de [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md) proporciona compatibilidad de manipulación de cadenas.  Se han diseñado para reemplazar y extender la funcionalidad proporcionada normalmente por el paquete de la cadena de la biblioteca en tiempo de ejecución de C.  El miembro de la clase de `CString` funciona y operadores para la cadena simplificada que administran, similares a los de básico.  La clase también proporciona constructores y operadores para crear, asignar, y comparar **CStrings** y tipos de datos estándar de la cadena de C\+\+.  Dado que `CString` no se deriva de `CObject`, puede utilizar los objetos de `CString` independientemente la biblioteca Microsoft Foundation Class \(MFC\).  
  
 los objetos de`CString` siguen la “semántica de valores”. Un objeto de `CString` representa un valor único.  Piense en `CString` como cadena real, no como un puntero a una cadena.  
  
 Un objeto de `CString` representa una secuencia de un número de caracteres variable.  Los objetos de`CString` se pueden considerar como matrices de caracteres.  
  
##  <a name="_core_unicode_and_mbcs_provide_portability"></a> Unicode y MBCS proporcionan Portabilidad  
 Con la versión 3,0 de MFC y después, MFC, incluidos `CString`, está habilitada para Unicode y los juegos de caracteres multibyte \(MBCS\).  Esta compatibilidad facilita para escribir aplicaciones portables que puede compilar en Unicode o caracteres ANSI.  Para habilitar esta portabilidad, cada carácter de un objeto de `CString` es de **TCHAR**con tipo, que se define como `wchar_t` si define el símbolo **\_UNICODE** cuando se compila la aplicación, o como `char` si no.  Un carácter de `wchar_t` es de 16 bits de ancho.  Se habilita MBCS si compila con el símbolo **\_MBCS** definido.  MFC se compila con el símbolo de **\_MBCS** \(para las bibliotecas de NAFX\) o el símbolo de **\_UNICODE** \(para las bibliotecas de UAFX\) definido.  
  
> [!NOTE]
>  Los ejemplos de `CString` en esta y los casos complementarios en cadenas muestran cadenas literales con formato correctamente para la portabilidad de Unicode, mediante la macro de **\_T** , cuáles traducen la cadena literal al formulario:  
  
 `L"literal string"`  
  
> [!NOTE]
>  lo que el compilador trata como cadena Unicode.  Por ejemplo, el código siguiente:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/CPP/string-data-management_1.cpp)]  
  
> [!NOTE]
>  se traduce como cadena Unicode si **\_UNICODE** se define o como una cadena ANSI si no.  Para obtener más información, vea el artículo [Compatibilidad con Unicode y con el juego de caracteres multibyte \(MBCS\)](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).  
  
 Un objeto de `CString` puede almacenar hasta **INT\_MAX** \(2.147.483.647\) caracteres.  Se usa el tipo de datos de **TCHAR** para obtener o establecer los caracteres individuales dentro de `CString` opóngase.  A diferencia de las matrices de caracteres, la clase de `CString` tiene una función integrada de asignación de memoria.  Esto permite que los objetos de `CString` crezcan automáticamente según sea necesario \(es decir, no tiene que preocuparse de llegar a un objeto de `CString` a cadenas más largas aptas\).  
  
##  <a name="_core_cstrings_and_const_char_pointers"></a> CStrings y const carbonizan punteros  
 Un objeto de `CString` también puede representar como una cadena literal de estilo C \( `PCXSTR`, que es igual que **const char\*** si no bajo Unicode\).  El operador de conversión de [CSimpleStringT::operator PCXSTR](../Topic/CSimpleStringT::operator%20PCXSTR.md) permite que los objetos de `CString` sean reemplazados libremente para punteros de carácter en llamadas de función.  El constructor de **CString\( LPCWSTR**`pszSrc`**\)** permite que los punteros de caracteres son reemplazados por los objetos de `CString` .  
  
 No se realiza ningún intento de doblar los objetos de `CString` .  Si crea dos objetos de `CString` que contienen `Chicago`, por ejemplo, los caracteres de `Chicago` se almacenan en dos lugares.  \(Esto no puede ser true de versiones futuras de MFC, por lo que no debe depender de\).  
  
> [!NOTE]
>  Utilice las funciones miembro de [CSimpleStringT::GetBuffer](../Topic/CSimpleStringT::GetBuffer.md) y de [CSimpleStringT::ReleaseBuffer](../Topic/CSimpleStringT::ReleaseBuffer.md) si necesita tener acceso directamente a `CString` como puntero que no es constante a un carácter.  
  
> [!NOTE]
>  Utilice las funciones miembro de [CStringT::AllocSysString](../Topic/CStringT::AllocSysString.md) y de [CStringT::SetSysString](../Topic/CStringT::SetSysString.md) para asignar y para establecer los objetos de `BSTR` utilizados en la automatización \(conocida antes como OLE Automation\).  
  
> [!NOTE]
>  Cuando sea posible, asigna los objetos de `CString` en el cuadro en lugar de en la pila.  Esto ahorra memoria y simplifica pasar parámetros.  
  
 La clase de `CString` no se implementa como una clase de colección de la biblioteca Microsoft Foundation Class, aunque los objetos de `CString` se pueden almacenar siempre como elementos en colecciones.  
  
##  <a name="_core_cstring_reference_counting"></a> Recuento de referencias de CString  
 A partir de la versión 4,0 de MFC, cuando se copian los objetos de [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md) , MFC incrementa el recuento de referencias en lugar de copiar los datos.  Esto crea pasar parámetros por valor y devolver los objetos de `CString` por valor más eficaz.  Estas operaciones hacen que el constructor de copias que se denomine, a veces más de una vez.  El incremento de un recuento de referencia reduce que sobrecarga para estas operaciones comunes y crea mediante `CString` una opción más atractiva.  
  
 Cuando se destruye cada copia, el recuento de referencias en el objeto original se reduzca.  El objeto de `CString` original no se destruye hasta que el recuento de referencias se reduzca a cero.  
  
 Puede utilizar las funciones [CSimpleStringT::LockBuffer](../Topic/CSimpleStringT::LockBuffer.md) y [CSimpleStringT::UnlockBuffer](../Topic/CSimpleStringT::UnlockBuffer.md) miembro de `CString` para deshabilitar o habilitar el recuento de referencias.  
  
## Vea también  
 [Temas generales de MFC](../mfc/general-mfc-topics.md)