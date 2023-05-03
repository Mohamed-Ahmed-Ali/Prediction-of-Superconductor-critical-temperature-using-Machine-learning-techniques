
# Predicting the temperature of a superconductor: Regression
By Mohamed Ali

### ABSTRACT
Superconductivity is a phenomenon of certain materials exhibiting zero electrical resistance and the expulsion of magnetic fields below a characteristic temperature1. It was discovered by Dutch physicist Heike Kamerlingh Onnes of Leiden University in 1911. Since then, many other superconducting materials have been discovered and the theory of superconductivity has been developed.
The connection between superconductivity and chemical/structural properties of materials remains poorly understood1. However, researchers have developed a machine learning model that predicts the critical temperatures (Tc) of superconducting material from the 21,000+ known superconductors available via the SuperCon database. The model uses features based only on the chemical compositions that were collected SuperCon database Then filtered the irrelevant features. A Regression models are developed to predict the values of Tc. It shows strong predictive power, with out-of-sample accuracy of about 92.5%. These models also demonstrate good performance, with learned predictors offering potential insights into the mechanisms behind superconductivity in different families of materials. <a href='https://www.sciencedirect.com/science/article/pii/S0927025618304877?via%3Dihub'>Another researcher</a> had gotten a root mean squared error (RMSE) of ±9.5kelvin on this data set, and this project's goal was to out perform this metric while comparing model techniques and analyzing features. This study was able to get ±9.2Kelvin RMSE. The data is originally sourced from the <a href='https://supercon.nims.go.jp/index_en.html'>superconducting material database</a>.

### Introduction
Superconductivity is a phenomenon in which certain materials exhibit zero electrical resistance and the expulsion of magnetic fields at very low temperatures. The discovery of superconductivity has led to numerous technological advancements in fields such as energy, transportation, and medicine. However, the critical temperature at which a material becomes a superconductor is highly dependent on its chemical properties, making it difficult to predict and optimize the superconducting properties of a material.

Superconductors have numerous practical applications, including in the fields of energy, transportation, and medical imaging. One of the most promising applications of superconductors is in the field of energy. Superconducting materials can be used to create efficient power transmission systems that can transport electricity over long distances with minimal losses. Superconducting magnets are also used in magnetic resonance imaging (MRI) machines for medical imaging.

Machine learning algorithms and techniques can be used to predict the critical temperature of superconductors based on their chemical composition. In this project, we use a dataset from the UCI Machine Learning Repository to train and evaluate regression models for predicting the critical temperature of superconductors based on their chemical composition. The project follows a step-by-step approach, beginning with data preprocessing, feature selection using a random forest model, and model training and evaluation using several regression algorithms. The evaluation metrics used include root mean squared error and R-squared score.

The results of this project can be used to optimize the superconducting properties of materials for practical applications. By accurately predicting the critical temperature, we can design and synthesize new superconducting materials with improved properties for specific applications.

<div id='background'></div>

### What is a superconductor? 

Superconductors and Critical Temperatures
A superconductor is a material that can conduct electricity with zero electrical resistance and without dissipating energy. This phenomenon occurs at very low temperatures, typically below a certain critical temperature, which varies depending on the material. Superconductors have numerous practical applications, including in the fields of energy, transportation, and medical imaging.

The critical temperature of a superconductor is a key property that determines its usefulness for practical applications. The critical temperature is the temperature at which a material transitions from a normal conductor to a superconductor. Materials with higher critical temperatures are more useful for practical applications since they can operate at higher temperatures, which makes them easier to cool and maintain.


<p align="center">
<img src = 'https://www.secretsofuniverse.in/wp-content/uploads/2020/07/quantum-levitation-1-1024x538-1.jpg' height='30%' width='60%'>
</p>


One of the most promising applications of superconductors is in the field of energy. Superconducting materials can be used to create efficient power transmission systems that can transport electricity over long distances with minimal losses. Superconducting magnets are also used in magnetic resonance imaging (MRI) machines for medical imaging.

Superconductors also have potential applications in transportation. Magnetic levitation (maglev) trains use superconducting magnets to levitate above a rail, eliminating friction and allowing for high-speed travel. Superconducting motors are also being developed for use in electric vehicles.

In addition to these applications, superconductors have potential uses in energy storage, quantum computing, and particle accelerators. However, the practical applications of superconductors are limited by the difficulty of producing materials with high critical temperatures and developing cost-effective production methods.

Machine learning algorithms and techniques can be used to predict the critical temperature of superconductors based on their chemical composition. This project uses a dataset from the UCI Machine Learning Repository to train and evaluate regression models for predicting the critical temperature of superconductors based on their chemical composition. The results of this project can be used to optimize the superconducting properties of materials for practical applications.

<div id='pre-processing'></div>

### Preprocessing the target variable: critical temperature

In this research project, the target variable was transformed to be approximately normal in order to improve the accuracy of the regression model. The original data was very positively skewed, which made it difficult to achieve a normal distribution. After a lot of trial and error, an exponential transformation was used to get the data (approximately) normal. Although there remained a slight skew in the best fit, the results observed at the end were quite good. The highest peak wasn’t simply an outlier and couldn’t be dropped or imputed
<p align="center">
<img src = 'https://i.imgur.com/JgVmNQ3.png'>
</p>

<div id='filtering'></div>

### Data

The project uses the Superconductivity Data Data Set from the SuperCon database. The dataset contains information on the chemical composition of 21,263 superconductors and their corresponding critical temperatures


number_of_elements|mean_atomic_mass|wtd_mean_atomic_mass|gmean_atomic_mass|wtd_gmean_atomic_mass|entropy_atomic_mass|wtd_entropy_atomic_mass|range_atomic_mass|wtd_range_atomic_mass|std_atomic_mass|wtd_std_atomic_mass|mean_fie|wtd_mean_fie|gmean_fie|wtd_gmean_fie|entropy_fie|wtd_entropy_fie|range_fie|wtd_range_fie|std_fie|wtd_std_fie|mean_atomic_radius|wtd_mean_atomic_radius|gmean_atomic_radius|wtd_gmean_atomic_radius|entropy_atomic_radius|wtd_entropy_atomic_radius|range_atomic_radius|wtd_range_atomic_radius|std_atomic_radius|wtd_std_atomic_radius|mean_Density|wtd_mean_Density|gmean_Density|wtd_gmean_Density|entropy_Density|wtd_entropy_Density|range_Density|wtd_range_Density|std_Density|wtd_std_Density|mean_ElectronAffinity|wtd_mean_ElectronAffinity|gmean_ElectronAffinity|wtd_gmean_ElectronAffinity|entropy_ElectronAffinity|wtd_entropy_ElectronAffinity|range_ElectronAffinity|wtd_range_ElectronAffinity|std_ElectronAffinity|wtd_std_ElectronAffinity|mean_FusionHeat|wtd_mean_FusionHeat|gmean_FusionHeat|wtd_gmean_FusionHeat|entropy_FusionHeat|wtd_entropy_FusionHeat|range_FusionHeat|wtd_range_FusionHeat|std_FusionHeat|wtd_std_FusionHeat|mean_ThermalConductivity|wtd_mean_ThermalConductivity|gmean_ThermalConductivity|wtd_gmean_ThermalConductivity|entropy_ThermalConductivity|wtd_entropy_ThermalConductivity|range_ThermalConductivity|wtd_range_ThermalConductivity|std_ThermalConductivity|wtd_std_ThermalConductivity|mean_Valence|wtd_mean_Valence|gmean_Valence|wtd_gmean_Valence|entropy_Valence|wtd_entropy_Valence|range_Valence|wtd_range_Valence|std_Valence|wtd_std_Valence|critical_temp|H|He|Li|Be|B|C|N|O|F|Ne|Na|Mg|Al|Si|P|S|Cl|Ar|K|Ca|Sc|Ti|V|Cr|Mn|Fe|Co|Ni|Cu|Zn|Ga|Ge|As|Se|Br|Kr|Rb|Sr|Y|Zr|Nb|Mo|Tc|Ru|Rh|Pd|Ag|Cd|In|Sn|Sb|Te|I|Xe|Cs|Ba|La|Ce|Pr|Nd|Pm|Sm|Eu|Gd|Tb|Dy|Ho|Er|Tm|Yb|Lu|Hf|Ta|W|Re|Os|Ir|Pt|Au|Hg|Tl|Pb|Bi|Po|At|Rn
---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---
4|88.9444675|57.862692285714296|66.36159243157189|36.1166119053847|1.1817952393305|1.06239554519617|122.90607|31.7949208571429|51.968827786103404|53.6225345301219|775.425|1010.26857142857|718.1528999521299|938.016780052204|1.30596703599158|0.791487788469155|810.6|735.9857142857139|323.811807806633|355.562966713294|160.25|105.514285714286|136.126003095455|84.528422716633|1.2592439721428899|1.2070399870146102|205|42.914285714285704|75.23754049674942|69.2355694829807|4654.35725|2961.5022857142894|724.953210852388|53.5438109235142|1.03312880053102|0.814598190091683|8958.571|1579.58342857143|3306.1628967555|3572.5966237083794|81.8375|111.72714285714301|60.1231785550982|99.4146820543113|1.15968659338134|0.7873816907632231|127.05|80.9871428571429|51.4337118896741|42.55839575195|6.9055|3.8468571428571403|3.4794748493632697|1.04098598567486|1.08857534188499|0.994998193254128|12.878|1.7445714285714298|4.599064116752451|4.66691955388659|107.75664499999999|61.0151885714286|7.06248773046785|0.62197948704754|0.308147989812345|0.262848266362233|399.97342000000003|57.12766857142861|168.854243757651|138.51716251123|2.25|2.25714285714286|2.2133638394006403|2.21978342968743|1.36892236074022|1.0662210317362|1|1.08571428571429|0.43301270189221897|0.43705881545081|29.0|0.0|0|0.0|0.0|0.0|0.0|0.0|4.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|1.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0.0|0.2|1.8|0.0|0.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0|0
5|92.729214|58.518416142857106|73.13278722250651|36.3966020291995|1.44930919335685|1.05775512271911|122.90607|36.161939000000004|47.094633170313394|53.9798696513451|766.44|1010.61285714286|720.605510513725|938.745412527433|1.5441445432697298|0.8070782149387309|810.6|743.164285714286|290.183029138508|354.963511171592|161.2|104.971428571429|141.465214777999|84.3701669575628|1.50832754035259|1.2041147982326001|205|50.571428571428605|67.321319060161|68.0088169554027|5821.4858|3021.01657142857|1237.09508033858|54.0957182556368|1.3144421846210501|0.9148021770663429|10488.571000000002|1667.3834285714302|3767.4031757706202|3632.64918471043|90.89|112.316428571429|69.8333146094209|101.166397739874|1.42799655342352|0.83866646563365|127.05|81.2078571428572|49.438167441765096|41.6676207979191|7.7844|3.7968571428571405|4.40379049753476|1.0352511158281401|1.37497728009085|1.07309384625263|12.878|1.59571428571429|4.473362654648071|4.60300005985449|172.20531599999998|61.37233142857139|16.0642278788044|0.6197346323305469|0.847404163195705|0.5677061078766371|429.97342000000003|51.4133828571429|198.554600255545|139.630922368904|2.0|2.25714285714286|1.8881750225898|2.2106794087065498|1.55711309805765|1.04722136819323|2|1.12857142857143|0.6324555320336761|0.468606270481621|26.0|0.0|0|0.0|0.0|0.0|0.0|0.0|4.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.9|0.0|0.0|0.0|0.0|0.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.1|0.0|0.0|0.0|0.0|0.0|0.0|0|0.0|0.1|1.9|0.0|0.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0|0
4|88.9444675|57.885241857142894|66.36159243157189|36.1225090359592|1.1817952393305|0.9759804641654979|122.90607|35.741099|51.968827786103404|53.65626773209821|775.425|1010.82|718.1528999521299|939.009035665864|1.30596703599158|0.773620193146673|810.6|743.164285714286|323.811807806633|354.804182855034|160.25|104.685714285714|136.126003095455|84.214573243296|1.2592439721428899|1.13254686280436|205|49.31428571428571|75.23754049674942|67.797712320685|4654.35725|2999.15942857143|724.953210852388|53.9740223651659|1.03312880053102|0.760305152674073|8958.571|1667.3834285714302|3306.1628967555|3592.01928133231|81.8375|112.213571428571|60.1231785550982|101.082152388012|1.15968659338134|0.7860067360250121|127.05|81.2078571428572|51.4337118896741|41.63987779712121|6.9055|3.8225714285714303|3.4794748493632697|1.03743942474191|1.08857534188499|0.927479442031317|12.878|1.75714285714286|4.599064116752451|4.64963546519334|107.75664499999999|60.94376|7.06248773046785|0.6190946827042739|0.308147989812345|0.250477444193951|399.97342000000003|57.12766857142861|168.854243757651|138.54061273834998|2.25|2.27142857142857|2.2133638394006403|2.23267852196607|1.36892236074022|1.02917468729772|1|1.11428571428571|0.43301270189221897|0.444696640464954|19.0|0.0|0|0.0|0.0|0.0|0.0|0.0|4.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|1.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0.0|0.1|1.9|0.0|0.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0|0
4|88.9444675|57.8739670714286|66.36159243157189|36.1195603503211|1.1817952393305|1.0222908923957|122.90607|33.7680099285714|51.968827786103404|53.63940496787|775.425|1010.54428571429|718.1528999521299|938.512776724546|1.30596703599158|0.7832066603612908|810.6|739.575|323.811807806633|355.18388442194396|160.25|105.1|136.126003095455|84.371352045645|1.2592439721428899|1.17303291789271|205|46.11428571428571|75.23754049674942|68.52166497852029|4654.35725|2980.33085714286|724.953210852388|53.758486291021796|1.03312880053102|0.7888885322214609|8958.571|1623.48342857143|3306.1628967555|3582.3705966440502|81.8375|111.970357142857|60.1231785550982|100.24495020209|1.15968659338134|0.7869004893749151|127.05|81.0975|51.4337118896741|42.1023442240235|6.9055|3.83471428571429|3.4794748493632697|1.0392111922717702|1.08857534188499|0.96403104867923|12.878|1.7445714285714298|4.599064116752451|4.658301352402599|107.75664499999999|60.97947428571429|7.06248773046785|0.6205354084838871|0.308147989812345|0.257045108326848|399.97342000000003|57.12766857142861|168.854243757651|138.528892724768|2.25|2.26428571428571|2.2133638394006403|2.2262216392083|1.36892236074022|1.04883427304761|1|1.1|0.43301270189221897|0.440952123830019|22.0|0.0|0|0.0|0.0|0.0|0.0|0.0|4.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|1.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0.0|0.15|1.85|0.0|0.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0|0
4|88.9444675|57.840142714285705|66.36159243157189|36.11071573753821|1.1817952393305|1.12922373013507|122.90607|27.8487427142857|51.968827786103404|53.5887706050743|775.425|1009.7171428571401|718.1528999521299|937.025572960086|1.30596703599158|0.8052296408133571|810.6|728.8071428571429|323.811807806633|356.31928137213|160.25|106.342857142857|136.126003095455|84.8434418389765|1.2592439721428899|1.26119371912948|205|36.514285714285705|75.23754049674942|70.63444843787241|4654.35725|2923.8451428571398|724.953210852388|53.1170285737926|1.03312880053102|0.859810869291435|8958.571|1491.78342857143|3306.1628967555|3552.6686635803203|81.8375|111.24071428571399|60.1231785550982|97.7747186271033|1.15968659338134|0.7873961825201741|127.05|80.76642857142859|51.4337118896741|43.4520592088545|6.9055|3.8711428571428597|3.4794748493632697|1.04454467078021|1.08857534188499|1.04496953590973|12.878|1.7445714285714298|4.599064116752451|4.6840139510763095|107.75664499999999|61.0866171428571|7.06248773046785|0.624877733754845|0.308147989812345|0.272819938850094|399.97342000000003|57.12766857142861|168.854243757651|138.493671473918|2.25|2.24285714285714|2.2133638394006403|2.20696281450132|1.36892236074022|1.0960519179005401|1|1.05714285714286|0.43301270189221897|0.42880945770867496|23.0|0.0|0|0.0|0.0|0.0|0.0|0.0|4.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|1.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0.0|0.3|1.7|0.0|0.0|0.0|0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0|0|0

### Preprocessing

The data is preprocessed by dropping highly correlated features and low-importance features, resulting in a final set of 36 features. The data is also standardized using the StandardScaler from the sklearn.preprocessing module.

number_of_elements|mean_atomic_mass|range_atomic_mass|wtd_range_atomic_mass|mean_fie|wtd_mean_fie|wtd_entropy_fie|range_fie|wtd_range_fie|mean_atomic_radius|wtd_range_atomic_radius|mean_Density|range_Density|mean_ElectronAffinity|wtd_mean_ElectronAffinity|range_ElectronAffinity|wtd_range_ElectronAffinity|mean_FusionHeat|range_FusionHeat|mean_ThermalConductivity|wtd_mean_ThermalConductivity|gmean_ThermalConductivity|wtd_entropy_ThermalConductivity|range_ThermalConductivity|range_Valence|wtd_range_Valence|critical_temp|O|S|Ca|Cu|Sr|Y|Ba|Tl|Bi
---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---
4.0|88.9444675|122.90607|31.7949208571429|775.425|1010.26857142857|0.791487788469155|810.6|735.9857142857139|160.25|42.914285714285704|4654.35725|8958.571|81.8375|111.72714285714301|127.05|80.9871428571429|6.9055|12.878|107.75664499999999|61.0151885714286|7.06248773046785|0.262848266362233|399.97342000000003|1.0|1.08571428571429|29.0|4.0|0.0|0.0|1.0|0.0|0.0|0.2|0.0|0.0
5.0|92.729214|122.90607|36.161939000000004|766.44|1010.61285714286|0.8070782149387309|810.6|743.164285714286|161.2|50.571428571428605|5821.4858|10488.571000000002|90.89|112.316428571429|127.05|81.2078571428572|7.7844|12.878|172.20531599999998|61.37233142857139|16.0642278788044|0.5677061078766371|429.97342000000003|2.0|1.12857142857143|26.0|4.0|0.0|0.0|0.9|0.0|0.0|0.1|0.0|0.0
4.0|88.9444675|122.90607|35.741099|775.425|1010.82|0.773620193146673|810.6|743.164285714286|160.25|49.31428571428571|4654.35725|8958.571|81.8375|112.213571428571|127.05|81.2078571428572|6.9055|12.878|107.75664499999999|60.94376|7.06248773046785|0.250477444193951|399.97342000000003|1.0|1.11428571428571|19.0|4.0|0.0|0.0|1.0|0.0|0.0|0.1|0.0|0.0
4.0|88.9444675|122.90607|33.7680099285714|775.425|1010.54428571429|0.7832066603612908|810.6|739.575|160.25|46.11428571428571|4654.35725|8958.571|81.8375|111.970357142857|127.05|81.0975|6.9055|12.878|107.75664499999999|60.97947428571429|7.06248773046785|0.257045108326848|399.97342000000003|1.0|1.1|22.0|4.0|0.0|0.0|1.0|0.0|0.0|0.15|0.0|0.0
4.0|88.9444675|122.90607|27.8487427142857|775.425|1009.7171428571401|0.8052296408133571|810.6|728.8071428571429|160.25|36.514285714285705|4654.35725|8958.571|81.8375|111.24071428571399|127.05|80.76642857142859|6.9055|12.878|107.75664499999999|61.0866171428571|7.06248773046785|0.272819938850094|399.97342000000003|1.0|1.05714285714286|23.0|4.0|0.0|0.0|1.0|0.0|0.0|0.3|0.0|0.0

<div id='model_selection'></div>

### Selecting the right model

Model Training and Evaluation
Several regression models are trained and evaluated, including ExtraTreesRegressor, Random Forest Regressor (rff), K-Nearest Neighbors (KNN), Bayesian Ridge, Ordinary Least Squares (OLS), Ridge, Lasso, and ElasticNet. The evaluation metrics used are root mean squared error (RMSE) and R-squared (R2) score.

* ExtraTreesRegressor
* Ordinary Least Squares
* Ridge Regression
* Lasso Regression
* Elastic Net regression
* Bayesian Ridge
* K-nearest neighbors regression
* Random Forest Regression


At each iteration the seven models were fit on a 70-30 train test split. The R2 and RMSE were then measured.

Graphing the evaluation metrics of each model as a function of the number of features used, we have;

<p align="center">
<img src='https://i.imgur.com/ZPDxyRC.png'>
</p>
The best performance metrics by each model were *(without tuning hyperparameters)*;

model|RMSE|R2 score|# of features used|time
---|---|---|---|---
RandomForestRegressor|8.804759|0.934204|29|6.92771
ExtraTreesRegressor|9.243836|0.927478|29|25.963824
KNN|15.140295|0.803092|14|0.094354
BayesianRidge|19.546809|0.677359|30|0.022965
OLS|19.547403|0.675702|29|0.019948
Ridge|19.547468|0.6757|29|0.00801
Lasso|19.88373|0.666141|30|0.647383
ElasticNet|20.087022|0.659279|30|0.615354


Thus, the best performing model (Random Forest regressor) was then fine tuned with it's hyperparameters.

<div id='rf'></div>

### Random Forest: Tuning hyperparameters

Because the main goal is to get the most accurate conclusions about superconductors, accuracy, in this context, is more important than efficiency. Hence, despite random forest regressor being the slowest model to fit the data (over 1 second), it was chosen to be the most important because it had the lowest loss function.

The hyperparameter that was tuned was the number of decision trees in the random forest. To do this,I again used a trial and error approach where I cycled through a range of forest sizes. In conjunction, I also tried using different 'max feature' parameters, specifically `log2`, `sqrt` and the default.

<p align="center">
<img src='https://i.imgur.com/z4E4hfJ.png'>
</p>

<div id='fitting'></div>

### Checking for a good fit

As in any regression analysis, R2 score and RMSE are not the only standards of evaluation. Examining the plot of the predicted values versus actual values is important, as is looking for normality and homoskedascity.

The plot of the predicted temperatures versus actual temperature was

<p align="center">
<img src='https://i.imgur.com/yClCcHB.png' height='30%' width='30%'>
</p>

### Feature Importance

A random forest model is used to determine the importance of each feature in predicting the target variable. The feature importance scores are used to rank the features and select the most important ones.

<p align="center">
<img src='https://i.imgur.com/Laef5i7.png'>
</p>
<div id='conclusions'></div>

### Results

The best performing regression model is the Random Forest model, which achieves an RMSE of 9.2 and an R2 score of 0.925. The power transformation of the critical temperature data improves the distribution of the data, resulting in a more normal distribution. The feature importances show that the chemical properties of Cu, O, and Ba are the most important predictors of the critical temperature.

<div id='codelinks'></div>

<div id='conclusions'></div>

### Conclusions

Machine learning algorithms and techniques can be used to predict the critical temperature of superconductors based on their chemical composition. The project demonstrates that the Random Forest model is the most accurate regression model for predicting the critical temperature of superconductors, achieving an RMSE of 9.2 and an R2 score of 0.925. The results of this project can be used to optimize the superconducting properties of materials for practical applications. Future work can explore other machine learning algorithms and techniques and investigate the effect of using different feature sets on the prediction accuracy.

<div id='codelinks'></div>

### Links to coded notebooks

* <a href='https://www.nature.com/articles/s41524-018-0085-8'> Machine learning modeling of superconducting critical temperature, by Valentin Stanev </a>
* <a href='https://www.sciencedirect.com/science/article/pii/S0927025618304877?via%3Dihub'>A data-driven statistical model for predicting the critical temperature of a superconductor, by Kam Hamidieh</a>
    * This was the other research I wanted to compare to.
* <a href ="https://archive.ics.uci.edu/ml/datasets/Superconductivty+Data#">UCI Machine learning repository on superconducting data</a>
    * The data can be downloaded from here.
* <a href ="https://supercon.nims.go.jp/index_en.html">Super conducting material database</a>
    * From the National Institute of Material Science; the organization that collected the data


    
