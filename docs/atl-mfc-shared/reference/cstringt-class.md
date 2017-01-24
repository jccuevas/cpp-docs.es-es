---
title: "CStringT Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CString"
  - "CStringT"
  - "ATL::CStringT"
  - "ATL.CStringT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStringT class"
  - "shared classes, CStringT"
  - "cadenas [C++], en ATL"
ms.assetid: 7cacc59c-425f-40f1-8f5b-6db921318ec9
caps.latest.revision: 33
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStringT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase representa un objeto de `CStringT` .  
  
## Sintaxis  
  
```  
  
      template< typename   
      BaseType  
      , class   
      StringTraits  
       >  
class CStringT :   
public CSimpleStringT<   BaseType,   _CSTRING_IMPL_::_MFCDLLTraitsCheck<      BaseType,      StringTraits   >   ::c_bIsMFCDLLTraits>  
```  
  
#### Parámetros  
 `BaseType`  
 El tipo de caracteres de la clase de cadena.  Puede ser una de las siguientes:  
  
-   `char` \(para las cadenas de caracteres ANSI\).  
  
-   `wchar_t` \(para las cadenas de caracteres Unicode\).  
  
-   **TCHAR** \(para ANSI y las cadenas de caracteres Unicode\).  
  
 `StringTraits`  
 Determina si la clase de cadena necesita la biblioteca en tiempo de ejecución de \(CRT\) C admiten y dónde se encuentran los recursos de cadena.  Puede ser una de las siguientes:  
  
-   **wchar\_t de StrTraitATL\<** &#124; `char` &#124; **TCHAR, wchar\_t de ChTraitsCRT\<** &#124; `char` &#124; **TCHAR \> \>**  
  
     La clase requiere compatibilidad y las búsquedas de CRT para las cadenas de recursos en el módulo especificado por `m_hInstResource` \(miembro de la clase de módulo de aplicación\).  
  
-   **wchar\_t de StrTraitATL\<** &#124; `char` &#124; **TCHAR, wchar\_t de ChTraitsOS\<** &#124; `char` &#124; **TCHAR \> \>**  
  
     La clase no necesita compatibilidad y las búsquedas de CRT para las cadenas de recursos en el módulo especificado por `m_hInstResource` \(miembro de la clase de módulo de aplicación\).  
  
-   **wchar\_t de StrTraitMFC\<** &#124; `char` &#124; **TCHAR, wchar\_t de ChTraitsCRT\<** &#124; `char` &#124; **TCHAR \> \>**  
  
     La clase requiere compatibilidad y las búsquedas de CRT para las cadenas de recursos mediante el algoritmo de búsqueda estándar de MFC.  
  
-   **wchar\_t de StrTraitMFC\<** &#124; `char` &#124; **TCHAR, wchar\_t de ChTraitsOS\<** &#124; `char` &#124; **TCHAR \> \>**  
  
     La clase no necesita compatibilidad y las búsquedas de CRT para las cadenas de recursos mediante el algoritmo de búsqueda estándar de MFC.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStringT::CStringT](../Topic/CStringT::CStringT.md)|Construye un objeto de `CStringT` de varias maneras.|  
|[CStringT::~CStringT](../Topic/CStringT::~CStringT.md)|Destruye un objeto `CStringT`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStringT::AllocSysString](../Topic/CStringT::AllocSysString.md)|Asigna `BSTR` de los datos de `CStringT` .|  
|[CStringT::AnsiToOem](../Topic/CStringT::AnsiToOem.md)|Crea una conversión en el contexto del juego de caracteres ANSI el juego de caracteres OEM.|  
|[CStringT::AppendFormat](../Topic/CStringT::AppendFormat.md)|Appends formateó datos a un objeto existente de `CStringT` .|  
|[CStringT::Collate](../Topic/CStringT::Collate.md)|Compara dos cadenas \(distingue entre mayúsculas y minúsculas, utiliza la información de la configuración regional\).|  
|[CStringT::CollateNoCase](../Topic/CStringT::CollateNoCase.md)|Compara dos cadenas \(sin distinción entre mayúsculas y minúsculas, utiliza la información de la configuración regional\).|  
|[CStringT::Compare](../Topic/CStringT::Compare.md)|Compara dos cadenas \(distingue entre mayúsculas y minúsculas\).|  
|[CStringT::CompareNoCase](../Topic/CStringT::CompareNoCase.md)|compara dos cadenas \(sin distinción entre mayúsculas y minúsculas\).|  
|[CStringT::Delete](../Topic/CStringT::Delete.md)|elimina un carácter o caracteres de una cadena.|  
|[CStringT::Find](../Topic/CStringT::Find.md)|Encuentra un carácter o una subcadena en una cadena mayor.|  
|[CStringT::FindOneOf](../Topic/CStringT::FindOneOf.md)|Encuentra el primer carácter coincidente de un conjunto.|  
|[CStringT::Format](../Topic/CStringT::Format.md)|Da formato a la cadena como hace `sprintf` .|  
|[CStringT::FormatMessage](../Topic/CStringT::FormatMessage.md)|Da formato a una cadena de mensaje.|  
|[CStringT::FormatMessageV](../Topic/CStringT::FormatMessageV.md)|Da formato a una cadena de mensaje mediante una lista de argumentos de variable.|  
|[CStringT::FormatV](../Topic/CStringT::FormatV.md)|Da formato a la cadena mediante una lista variable de argumentos.|  
|[CStringT::GetEnvironmentVariable](../Topic/CStringT::GetEnvironmentVariable.md)|Establece la cadena el valor de la variable de entorno especificada.|  
|[CStringT::Insert](../Topic/CStringT::Insert.md)|Inserta un carácter o una subcadena en el índice especificado en la cadena.|  
|[CStringT::Left](../Topic/CStringT::Left.md)|Extrae la parte izquierda de una cadena.|  
|[CStringT::LoadString](../Topic/CStringT::LoadString.md)|carga un objeto existente de `CStringT` de un recurso de Windows.|  
|[CStringT::MakeLower](../Topic/CStringT::MakeLower.md)|Convierte todos los caracteres de la cadena a caracteres en minúsculas.|  
|[CStringT::MakeReverse](../Topic/CStringT::MakeReverse.md)|invierte la cadena.|  
|[CStringT::MakeUpper](../Topic/CStringT::MakeUpper.md)|Convierte todos los caracteres de la cadena a caracteres en mayúscula.|  
|[CStringT::Mid](../Topic/CStringT::Mid.md)|Extrae la parte media de una cadena.|  
|[CStringT::OemToAnsi](../Topic/CStringT::OemToAnsi.md)|Crea una conversión en el contexto del juego de caracteres OEM el juego de caracteres ANSI.|  
|[CStringT::Remove](../Topic/CStringT::Remove.md)|Quita indicó caracteres de una cadena.|  
|[CStringT::Replace](../Topic/CStringT::Replace.md)|Replaces indicó caracteres con otros caracteres.|  
|[CStringT::ReverseFind](../Topic/CStringT::ReverseFind.md)|Encuentra un carácter en una cadena mayor; sale del extremo.|  
|[CStringT::Right](../Topic/CStringT::Right.md)|Extrae la parte derecha de una cadena.|  
|[CStringT::SetSysString](../Topic/CStringT::SetSysString.md)|establece un objeto existente de `BSTR` con datos de un objeto de `CStringT` .|  
|[CStringT::SpanExcluding](../Topic/CStringT::SpanExcluding.md)|extrae los caracteres de la cadena, empezando por el primer carácter, que no están en el conjunto de caracteres identificados por `pszCharSet`.|  
|[CStringT::SpanIncluding](../Topic/CStringT::SpanIncluding.md)|Dibuja una subcadena que contiene únicamente caracteres en un conjunto.|  
|[CStringT::Tokenize](../Topic/CStringT::Tokenize.md)|Extrae tokens especificado en la cadena de destino.|  
|[CStringT::Trim](../Topic/CStringT::Trim.md)|Corta todos los caracteres iniciales y finales en blanco la cadena.|  
|[CStringT::TrimLeft](../Topic/CStringT::TrimLeft.md)|Ajustes que conducen los caracteres de espacio en blanco de la cadena.|  
|[CStringT::TrimRight](../Topic/CStringT::TrimRight.md)|Ajustes que arrastre los caracteres de espacio en blanco de la cadena.|  
  
### Operadores  
  
|||  
|-|-|  
|[CStringT::operator \=](../Topic/CStringT::operator%20=.md)|asigna un nuevo valor a un objeto de `CStringT` .|  
|[CStringT::operator \+](../Topic/CStringT::operator%20+.md)|concatena dos cadenas o un carácter y una cadena.|  
|[CStringT::operator \+\=](../Topic/CStringT::operator%20+=.md)|Concatena una nueva cadena al final de una cadena existente.|  
|[CStringT::operator \=\=](../Topic/CStringT::operator%20==.md)|determina si dos cadenas son lógicamente iguales.|  
|[CStringT::operator \!\=](../Topic/CStringT::operator%20!=.md)|determina si dos cadenas no son lógicamente iguales.|  
|[CStringT::operator \<](../Topic/CStringT::operator%20%3C.md)|Determina si la cadena en el lado izquierdo del operador es menor que la cadena en el lado derecho.|  
|[CStringT::operator \>](../Topic/CStringT::operator%20%3E.md)|Determina si la cadena en el lado izquierdo del operador es mayor que la cadena en el lado derecho.|  
|[CStringT::operator \<\=](../Topic/CStringT::operator%20%3C=.md)|Determina si la cadena en el lado izquierdo del operador menor o igual que la cadena en el lado derecho.|  
|[CStringT::operator \>\=](../Topic/CStringT::operator%20%3E=.md)|Determina si la cadena en el lado izquierdo del operador mayor o igual que la cadena en el lado derecho.|  
  
## Comentarios  
 `CStringT` hereda de [clase de CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md).  Las características avanzadas, como la manipulación de carácter, ordenar, y busque, se implementan en `CStringT`.  
  
> [!NOTE]
>  los objetos de`CStringT` son capaces de producir excepciones.  Esto ocurre cuando se ejecuta un objeto de `CStringT` fuera de memoria por cualquier motivo.  
  
 Un objeto de `CStringT` consta de una secuencia de longitud variable de caracteres.  `CStringT` proporciona funciones y operadores mediante la sintaxis similar a la de básico.  Concatenación y los operadores de comparación, así como la administración de memoria simplificada, crean los objetos de `CStringT` más fáciles de utilizar que las matrices de caracteres normales.  
  
> [!NOTE]
>  Aunque es posible crear instancias de `CStringT` que contienen caracteres nulos incrustados, recomendamos con ellos.  Los métodos y operadores de los objetos de `CStringT` que contienen caracteres nulos incrustados pueden generar resultados imprevistos.  
  
 Usar distintas combinaciones de parámetros de `BaseType` y de `StringTraits` , los objetos de `CStringT` pueden crecer en los siguientes tipos, que se han sido predefinidos por las bibliotecas de ATL.  
  
 Si utiliza en una aplicación ATL:  
  
 `CString`, `CStringA`, y `CStringW` se exportan DLL de MFC \(MF C90 .DLL\), nunca de las DLL de usuario.  Esto es necesario para evitar que `CStringT` sea multiplicar definido.  
  
> [!NOTE]
>  Si se produjo errores del vinculador para exportar `CString`\- clase derivada de un archivo DLL de extensión MFC en Visual C\+\+ .NET 2002 y ha aplicado la solución alternativa como se describe en el artículo de Knowledge Base, “vinculando clases CString\-Derivadas de importación Cuando Se de errores” \(Q309801\), debe quitar el código de la solución, porque esto se ha solucionado en Visual C\+\+ .NET 2003.  Encontrará artículos de Knowledge Base en el CD\-ROM de MSDN Library o en la dirección [http:\/\/support.microsoft.com\/support](http://support.microsoft.com/support).  
  
 Los tipos de cadena siguientes están disponibles en las aplicaciones basadas:  
  
|tipo de CStringT|Declaración|  
|----------------------|-----------------|  
|`CStringA`|Un tipo string de caracteres ANSI con compatibilidad de CRT.|  
|`CStringW`|Un tipo de cadena de caracteres Unicode con compatibilidad de CRT.|  
|`CString`|ANSI y los tipos de caracteres Unicode con compatibilidad de CRT.|  
  
 Los tipos de cadena siguientes están disponibles en proyectos donde se define **ATL\_CSTRING\_NO\_CRT** :  
  
|tipo de CStringT|Declaración|  
|----------------------|-----------------|  
|**CAtlStringA**|Un tipo string de caracteres ANSI sin compatibilidad de CRT.|  
|**CAtlStringW**|Un tipo de cadena de caracteres Unicode sin compatibilidad de CRT.|  
|**CAtlString**|ANSI y los tipos de caracteres Unicode sin compatibilidad de CRT.|  
  
 Los tipos de cadena siguientes están disponibles en proyectos donde no está definido **ATL\_CSTRING\_NO\_CRT** :  
  
|tipo de CStringT|Declaración|  
|----------------------|-----------------|  
|**CAtlStringA**|Un tipo string de caracteres ANSI con compatibilidad de CRT.|  
|**CAtlStringW**|Un tipo de cadena de caracteres Unicode con compatibilidad de CRT.|  
|**CAtlString**|ANSI y los tipos de caracteres Unicode con compatibilidad de CRT.|  
  
 los objetos de`CString` también tienen las siguientes características:  
  
-   los objetos de`CStringT` pueden crecer como resultado de las operaciones de concatenación.  
  
-   los objetos de`CStringT` siguen la “semántica de valores”. Piense en un objeto de `CStringT` como cadena real, no como un puntero a una cadena.  
  
-   Puede sustituir libremente los objetos de `CStringT` para los argumentos de la función de `PCXSTR` .  
  
-   Administración de memoria personalizada para los búferes de cadenas.  Para obtener más información, vea [administración de memoria y CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
## CStringT los tipos  
 Dado que `CStringT` utiliza un argumento de plantilla para definir el tipo de carácter \( [wchar\_t](../../c-runtime-library/standard-types.md) o [char](../../c-runtime-library/standard-types.md)\) admite, los tipos de parámetro de método pueden ser más complejos a veces.  Para simplificar este problema, un conjunto de tipos predefinidos se define y se usa en la clase de `CStringT` .  La tabla siguiente se enumeran los tipos diferentes:  
  
|Name|Descripción|  
|----------|-----------------|  
|`XCHAR`|Un carácter individual \( `wchar_t` o `char`\) con el mismo tipo de caracteres que el objeto de `CStringT` .|  
|**YCHAR**|Un carácter individual \( `wchar_t` o `char`\) con el tipo de carácter opuesto como objeto de `CStringT` .|  
|`PXSTR`|Un puntero a una cadena de caracteres \( `wchar_t` o `char`\) con el mismo tipo de caracteres que el objeto de `CStringT` .|  
|**PYSTR**|Un puntero a una cadena de caracteres \( `wchar_t` o `char`\) con el tipo de carácter opuesto como objeto de `CStringT` .|  
|`PCXSTR`|Un puntero a una cadena de caracteres **const** \( `wchar_t` o `char`\) con el mismo tipo de caracteres que el objeto de `CStringT` .|  
|**PCYSTR**|Un puntero a una cadena de caracteres **const** \( `wchar_t` o `char`\) con el tipo de carácter opuesto como objeto de `CStringT` .|  
  
> [!NOTE]
>  El código que utilizó anteriormente métodos indocumentados de `CString` \(como **AssignCopy**\) se debe reemplazar con el código que utiliza los métodos documentados siguientes de `CStringT` \(como `GetBuffer` o `ReleaseBuffer`\).  estos métodos se heredan de `CSimpleStringT`.  
  
## Jerarquía de herencia  
 [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)  
  
 `CStringT`  
  
## Requisitos  
  
|Encabezado|Se utiliza para|  
|----------------|---------------------|  
|cstringt.h|Objetos de cadena de MFC\-solamente|  
|atlstr.h|Objetos string de MFC|  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)   
 [CSimpleStringT Class](../../atl-mfc-shared/reference/csimplestringt-class.md)