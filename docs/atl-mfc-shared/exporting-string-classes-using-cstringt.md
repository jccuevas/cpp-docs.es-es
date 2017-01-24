---
title: "Exporting String Classes Using CStringT | Microsoft Docs"
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
  - "CStringT class, exporting strings"
ms.assetid: bdfc441e-8d2a-461c-9885-46178066c09f
caps.latest.revision: 15
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exporting String Classes Using CStringT
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el pasado, los desarrolladores de MFC tienen derivado de `CString` especializar sus propias clases de la cadena.  En Microsoft Visual C\+\+ .NET \(MFC 8,0\), la clase de [CString](../atl-mfc-shared/using-cstring.md) se sustituye por una clase de plantilla con [CStringT](../atl-mfc-shared/reference/cstringt-class.md).  Esto proporciona varias ventajas:  
  
-   Permitía que la clase MFC `CString` se usó en proyectos ATL sin vinculación en la biblioteca estática mayor o DLL de MFC.  
  
-   Con la nueva clase de plantilla de `CStringT` , puede personalizar el comportamiento de `CString` mediante los parámetros de plantilla que especifican rasgos de carácter, similares a las plantillas en la biblioteca de \(STL\) plantillas estándar.  
  
-   Cuando exporta posee la clase de cadena de un archivo DLL mediante `CStringT`, el compilador también se exporta automáticamente la clase base de `CString` .  Puesto que `CString` es una clase de plantilla, se pueden crear instancias del compilador cuando se utiliza, a menos que el compilador tenga en cuenta que `CString` se importa de DLL.  Si se ha migrado proyectos de Visual C\+\+ 6,0 y Visual C\+\+ .NET, es posible que haya visto los errores de símbolos del vinculador para `CString` multiplicar\-definido debido a la colisión de `CString` importar desde un archivo DLL y la versión localmente crear instancias.  La manera adecuada de ello se describe a continuación.  Para obtener más información sobre este problema, vea el artículo de Knowledge Base, “vinculando errores cuando se importa clases CString\-derivadas” \(Q309801\) en el CD\-ROM de MSDN Library o en [http:\/\/support.microsoft.com\/default.aspx](http://support.microsoft.com/default.aspx).  
  
 El escenario siguiente provocará el vinculador a errores de símbolos de producción para multiplica clases definidas.  Suponga que exporte `CString`\- clase derivada \(`CMyString`\) de un archivo DLL de extensión de MFC:  
  
 [!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/CPP/exporting-string-classes-using-cstringt_1.cpp)]  
  
 El código del consumidor utiliza una combinación de `CString` y de `CMyString`. "  MyString.h” no se incluye en el encabezado precompilado, y el uso de `CString` no tiene `CMyString` visible.  
  
 Suponga que utiliza las clases de `CString` y de `CMyString` en los archivos de código fuente independientes, Source1.cpp y Source2.cpp.  En Source1.cpp, se utiliza `CMyString` y \#include MyString.h.  En Source2.cpp, se utiliza `CString`, pero no \#include MyString.h.  en este caso, el vinculador se quejará por `CStringT` que es multiplica definido.  El está provocado por `CString` que se está importando de DLL que exporta `CMyString`, y creado instancias localmente por el compilador mediante la plantilla de `CStringT` .  
  
 Para resolver este problema, haga lo siguiente:  
  
 Exportar `CStringA` y `CStringW` \(y clases base necesarias\) MF C90 .DLL.  Proyectos que incluyan MFC usarán siempre MFC `CStringA` exportado DLL y `CStringW`, como en las implementaciones anteriores de MFC.  
  
 A continuación cree una clase derivada exportable mediante la plantilla de `CStringT` , mientras que `CStringT_Exported` está presionada, por ejemplo:  
  
 [!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/CPP/exporting-string-classes-using-cstringt_2.cpp)]  
  
 En AfxStr.h, reemplace `CString`anterior, `CStringA`, y tipos de `CStringW` como sigue:  
  
 [!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/CPP/exporting-string-classes-using-cstringt_3.cpp)]  
  
 hay varias advertencias:  
  
-   No debe exportar `CStringT` propio porque esto hará que los proyectos de ATL\-only de exportar una clase especializada de `CStringT` .  
  
-   Mediante una clase derivada exportable de `CStringT` minimiza tenían que funcionalidad de `CStringT` de re\-instrumento.  El código adicional se limita a reenviar constructores a la clase base de `CStringT` .  
  
-   `CString`, `CStringA`, y `CStringW` deben sólo se `__declspec(dllexport/dllimport)` marcado cuando está compilando con DLL compartido MFC.  Si vincula con una biblioteca estática de MFC, no debe marcar estas clases según lo exportado; si no, el uso interno de `CString`, de `CStringA`, y de `CStringW` dentro de los archivos DLL de usuario marcará `CString` como exportado también.  
  
## Temas relacionados  
 [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md)  
  
## Vea también  
 [Using CStringT](../atl-mfc-shared/using-cstringt.md)   
 [Using CString](../atl-mfc-shared/using-cstring.md)