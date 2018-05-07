---
title: CSQLLanguages, CSQLLanguageInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSQLLanguageInfo
- m_szProgrammingLanguage
- m_szImplementation
- m_szIntegrity
- m_szBindingStyle
- m_szConformance
- m_szSource
- m_szYear
- CSQLLanguages
dev_langs:
- C++
helpviewer_keywords:
- m_szBindingStyle
- m_szProgrammingLanguage
- m_szYear
- m_szImplementation
- m_szSource
- m_szConformance
- CSQLLanguages typedef class
- CSQLLanguageInfo parameter class
- m_szIntegrity
ms.assetid: 9c36c5bb-6917-49c3-9ac3-942339893f19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 214cd5b1a4554d90ac21a87aad0951a21126af4d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="csqllanguages-csqllanguageinfo"></a>CSQLLanguages, CSQLLanguageInfo
Llamar a la clase de typedef **CSQLLanguages** para implementar su clase de parámetro **CSQLLanguageInfo**.  
  
## <a name="remarks"></a>Comentarios  
 Vea [clases de conjunto de filas de esquema y clases Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) para obtener más información sobre el uso de clases typedef.  
  
 Esta clase identifica los niveles de compatibilidad, opciones y dialectos admitidos por los datos de procesamiento de la implementación de SQL definidos en el catálogo.  
  
 En la tabla siguiente se enumera los miembros de datos de la clase y sus columnas OLE DB correspondiente. Vea [conjunto de filas SQL_LANGUAGES](https://msdn.microsoft.com/en-us/library/ms714374.aspx) en el *referencia del programador de OLE DB* para obtener más información sobre el esquema y las columnas.  
  
|Miembros de datos|Columnas de OLE DB|  
|------------------|--------------------|  
|m_szSource|SQL_LANGUAGE_SOURCE|  
|m_szYear|SQL_LANGUAGE_YEAR|  
|m_szConformance|SQL_LANGUAGE_CONFORMANCE|  
|m_szIntegrity|SQL_LANGUAGE_INTEGRITY|  
|m_szImplementation|SQL_LANGUAGE_IMPLEMENTATION|  
|m_szBindingStyle|SQL_LANGUAGE_BINDING_STYLE|  
|m_szProgrammingLanguage|SQL_LANGUAGE_PROGRAMMING_LANGUAGE|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbsch.h  
  
## <a name="see-also"></a>Vea también  
 [CRestrictions (Clase)](../../data/oledb/crestrictions-class.md)