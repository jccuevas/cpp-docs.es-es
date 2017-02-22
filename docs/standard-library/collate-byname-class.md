---
title: "collate_byname (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::collate_byname"
  - "locale/std::collate_byname"
  - "std.collate_byname"
  - "collate_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "collate_byname (clase)"
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# collate_byname (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

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
 Un recuento de referencia inicial.  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla describe un objeto que puede actuar como un [faceta de configuración regional](../standard-library/locale-class.md#facet_class) de tipo [collate](../standard-library/collate-class.md#collate__collate)\< CharType>. Su comportamiento viene determinado por la [denominado](../standard-library/locale-class.md#locale__name) Configuración regional `_Locname`. Cada constructor inicializa su objeto base con [collate](../standard-library/collate-class.md#collate__collate)\< CharType>( `_Refs`).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \< configuración regional>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



