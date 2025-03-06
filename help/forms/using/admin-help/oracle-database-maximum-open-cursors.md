---
title: Schwellenwert für die Anzahl maximal geöffneter Cursor für Oracle-Datenbank
description: Erfahren Sie mehr über die Konfiguration eines Maximalwerts für geöffnete Cursors in Oracle.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 98663f16-6c05-4485-9bf2-a2de9d1975c8
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '82'
ht-degree: 100%

---

# Schwellenwert für die Anzahl maximal geöffneter Cursor für Oracle-Datenbank {#oracle-database-maximum-open-cursors-threshold}

Um einen Maximalwert für geöffnete Cursors in Oracle zu konfigurieren, müssen Sie diesen Wert möglicherweise auf eine Zahl einstellen, die für Ihre Anwendung geeignet ist.  Es ist offensichtlich, dass die durchschnittliche Anzahl geöffneter Cursors bei mittlerer Auslastung 2700 betrug.  Es wird empfohlen, mit einem oberen Grenzwert von 3000 zu beginnen.  Weitere Informationen finden Sie unter [https://www.orafaq.com/node/758](https://www.orafaq.com/node/758).
