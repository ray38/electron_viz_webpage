# Electronic Enviroment Visualization Tool

This tool is developed to visualize electronic environment data generated from Density Functional Theory (DFT). 

It will load the x,y,z coordinates, electronic density, plus other properties of a molecular system from the data file, and display the system in 3D point cloud. The density of the points corresponds to the electronic density. The color of the points is highly customizable, and it could be based on various color scheme and property of choice.

The tool also could plot 2D plots (2D heatmaps) based on the properties of interest. One can select a region in the 2D plot, and the corresponding points would also be selected and highlighted in the 3D views.

Moreover, the tool supports viewing multiple systems and multiple 2D plots at the same time.

This tool is developed mainly with [three.js](https://threejs.org/), and wrapped with [elecrtron.js](https://electronjs.org/)

## Video

## Workflows
first the tool will read the `view_setup.js` file as a input. Something like this:
```
var views = [
	{
		viewType: '3DView',
		moleculeName: 'CO2',
		dataFilename: "data/CO2_B3LYP_0_0_0_all_descriptors.csv"
	},
	{
		viewType: '3DView',
		moleculeName: 'H2O',
		dataFilename: "data/H2O_B3LYP_0_0_0_all_descriptors.csv"
	},
	{
		viewType: '2DHeatmap',
		plotX: 'gamma',
		plotY: 'epxc',
		plotXTransform: 'linear',
		plotYTransform: 'linear'
	},
	{
		viewType: '2DHeatmap',
		plotX: 'n',
		plotY: 'epxc',
		plotXTransform: 'linear',
		plotYTransform: 'linear'
	}
];
```
The user can change this file to visualize their own data
The tool loads all the data files for the 3D Views and pool them together, before compiling the 2D heatmaps with the pooled data.

The user can rotate/pan/zoom the 3D views, and pan/zoom the 2D plots


The user can customize the view of the views



The user can toggle fullscreen for any one of the views to see the details



The user can drag a selecton brush on any of the 2D heatmaps, and other views will update simutaneously. The corresponding regions of the selected points will be highlighted on the 3D views.




The user can hide/show the tool boxes by pressing `h`




## Implementation Details

The whole package was written in Javascript as a Web app, and then wrapped with `electron.js` to make it a desktop app.. All the 3D point clouds and 2D heatmaps are generated with `Three.js`, but some functions of `D3.js` were also used. The tool boxes are implemented using `dat.gui`. 

The code were brokedown into small files with `ES6/ES2015` import/export feature. Considering the browser compatibility, we transpile the JS files to `ES5` using `Babel + browserify`. 

## Future goals 

- Clean up the `selection` function of hte 2D plots
- Add more selection method
- make it so that the user can upload the view setup file instead of hard-coding it. something like this [example](http://bl.ocks.org/phil-pedruco/9913243)
- including more views for the 3D part



### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/ray38/electron_viz_webpage/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
