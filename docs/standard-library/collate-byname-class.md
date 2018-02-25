---
title: collate_byname (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- locale/std::collate_byname
dev_langs:
- C++
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2682abebd6528edbdbec1f6fb1a00082436f1299
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="collatebyname-class"></a>collate_byname (Clase)
Una clase de plantilla derivada que describe un objeto que puede actuar como una faceta de intercalación de una configuración regional concreta, lo que permite la recuperación de información específica de un área cultural relativa a las convenciones de ordenación de cadenas.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class CharType>
class collate_byname : public collate<CharType> {
public:
    explicit collate_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit collate_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~collate_byname();

};
```  
  
#### <a name="parameters"></a>Parámetros  
 `_Locname`  
 Una configuración regional con nombre.  
  
 `_Refs`  
 Un recuento de referencias inicial.  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla describe un objeto que puede actuar como una [faceta de configuración regional](../standard-library/locale-class.md#facet_class) de tipo [collate](../standard-library/collate-class.md#collate)\<CharType>. Su comportamiento viene determinado por la configuración regional [con nombre](../standard-library/locale-class.md#name) `_Locname`. Cada constructor inicializa su objeto base con [collate](../standard-library/collate-class.md#collate)\<CharType>( `_Refs`).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<locale>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



