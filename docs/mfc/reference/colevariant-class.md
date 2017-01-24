---
title: "COleVariant Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleVariant"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "automatización, tipos de parámetros"
  - "COleVariant class"
  - "VARIANT data type"
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleVariant Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

encapsula el tipo de datos de [VARIANT](http://msdn.microsoft.com/es-es/e305240e-9e11-4006-98cc-26f4932d2118) .  
  
## Sintaxis  
  
```  
class COleVariant : public tagVARIANT  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleVariant::COleVariant](../Topic/COleVariant::COleVariant.md)|Crea un objeto `COleVariant`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleVariant::Attach](../Topic/COleVariant::Attach.md)|Asocia **VARIANT** a `COleVariant`.|  
|[COleVariant::ChangeType](../Topic/COleVariant::ChangeType.md)|cambia el tipo variable de este objeto de `COleVariant` .|  
|[COleVariant::Clear](../Topic/COleVariant::Clear.md)|Borra este objeto `COleVariant`.|  
|[COleVariant::Detach](../Topic/COleVariant::Detach.md)|desasocia **VARIANT** de `COleVariant` y devuelve **VARIANT**.|  
|[COleVariant::GetByteArrayFromVariantArray](../Topic/COleVariant::GetByteArrayFromVariantArray.md)|Recupera una matriz de bytes de una matriz variable existente.|  
|[COleVariant::SetString](../Topic/COleVariant::SetString.md)|Establece la cadena en un tipo determinado, normalmente ANSI.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleVariant::operator LPCVARIANT](../Topic/COleVariant::operator%20LPCVARIANT.md)|convierte un valor de `COleVariant` en `LPCVARIANT`.|  
|[COleVariant::operator LPVARIANT](../Topic/COleVariant::operator%20LPVARIANT.md)|convierte un objeto de `COleVariant` en `LPVARIANT`.|  
|[COleVariant::operator \=](../Topic/COleVariant::operator%20=.md)|copia un valor de `COleVariant` .|  
|[COleVariant::operator \=\=](../Topic/COleVariant::operator%20==.md)|compara dos valores de `COleVariant` .|  
|[COleVariant::operator \<\<, \>\>](../Topic/COleVariant::operator%20%3C%3C,%20%3E%3E.md)|genera un valor de `COleVariant` a `CArchive` o a `CDumpContext` y entradas un objeto de `COleVariant` de `CArchive`.|  
  
## Comentarios  
 Utilizan este tipo de datos de automatización OLE.  Específicamente, la estructura de [DISPPARAMS](http://msdn.microsoft.com/es-es/a16e5a21-766e-4287-b039-13429aa78f8b) contiene un puntero a una matriz de estructuras de **VARIANT** .  una estructura de **DISPPARAMS** se utiliza para pasar parámetros a [IDispatch::Invoke](http://msdn.microsoft.com/es-es/964ade8e-9d8a-4d32-bd47-aa678912a54d).  
  
> [!NOTE]
>  Esta clase se deriva de la estructura de **VARIANT** .  Esto significa que puede pasar `COleVariant` en un parámetro que pide **VARIANT** y que sean miembros de datos los miembros de datos de la estructura de **VARIANT** accesibles de `COleVariant`.  
  
 Las dos clases MFC relacionadas [COleCurrency](../../mfc/reference/colecurrency-class.md) y [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) encapsulan tipos de datos variables **Moneda** \(`VT_CY`\) y **DATE** \(`VT_DATE`\).  La clase de `COleVariant` se usa ampliamente en las clases DAO; vea estas clases para el uso típico de esta clase, por ejemplo [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) y [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).  
  
 Para obtener más información, vea [VARIANT](http://msdn.microsoft.com/es-es/e305240e-9e11-4006-98cc-26f4932d2118), [Moneda](http://msdn.microsoft.com/es-es/5e81273c-7289-45c7-93c0-32c1553f708e), [DISPPARAMS](http://msdn.microsoft.com/es-es/a16e5a21-766e-4287-b039-13429aa78f8b), y las entradas de [IDispatch::Invoke](http://msdn.microsoft.com/es-es/964ade8e-9d8a-4d32-bd47-aa678912a54d) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Para obtener más información sobre la clase de `COleVariant` y su uso en la automatización OLE, vea “pasar parámetros en la automatización OLE” en el artículo [automatización](../../mfc/automation.md).  
  
## Jerarquía de herencia  
 `tagVARIANT`  
  
 `COleVariant`  
  
## Requisitos  
 **encabezado:** afxdisp.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)