# PubTabNet

PubTabNet is a large dataset for image-based table recognition, containing 568k+ images of tabular data annotated with the corresponding HTML representation of the tables. The table images are extracted from the scientific publications included in the [PubMed Central Open Access Subset (commercial use collection)](https://www.ncbi.nlm.nih.gov/pmc/tools/openftlist/). Table regions are identified by matching the PDF format and the XML format of the articles in the PubMed Central Open Access Subset. More details are available in our paper ["Image-based table recognition: data, model, and evaluation"](https://arxiv.org/abs/1911.10683).

## Updates in progress

### Encoder-dual-decoder model

In our paper, we proposed a new encoder-dual-decoder architecture, which was trained on PubTabNet and can accurately reconstruct the HTML representation of complex tables solely relying on image input. We are working on legal approval for releasing the source code and the pre-trained model on [IBM Model Asset eXchange (MAX)](https://developer.ibm.com/exchanges/models/).  

### Ground truth of test set

The ground truth of test will not be release, as we want to keep it for a competition in the future. We will offer a service for people to submit and evaluate their results soon.

## Getting data

Images and annotations can be downloaded [here](https://developer.ibm.com/exchanges/data/all/pubtabnet/). If you want to download the data from the command line, you can use curl or wget to download the data.

```
curl -o <YOUR_TARGET_DIR>/PubTabNet.tar.gz https://dax-cdn.cdn.appdomain.cloud/dax-pubtabnet/1.0.1/PubTabNet.tar.gz
```

```
wget -O <YOUR_TARGET_DIR>/PubTabNet.tar.gz https://dax-cdn.cdn.appdomain.cloud/dax-pubtabnet/1.0.1/PubTabNet.tar.gz
```

## Annotation structure

The structure of the annotation json file is:

```
{'dataset': str,
 'images': [
   'filename': str,
   'split': str,
   'imgid': int,
   'html': {
     'structure': {'tokens': [str]},
     'cell': [
       {'tokens': [str]}
     ]
   }
 ]
}
```

## Cite us

```
@article{zhong2019image,
  title={Image-based table recognition: data, model, and evaluation},
  author={Zhong, Xu and ShafieiBavani, Elaheh and Yepes, Antonio Jimeno},
  journal={arXiv preprint arXiv:1911.10683},
  year={2019}
}
```

## Examples

A [Jupyter notebook](./explore_PubTabNet_dataset.ipynb) is provided to inspect the annotations of 20 sample tables.


## Related links

[PubLayNet](https://github.com/ibm-aur-nlp/PubLayNet) is a large dataset of document images, of which the layout is annotated with both bounding boxes and polygonal segmentations. The source of the documents is [PubMed Central Open Access Subset (commercial use collection)](https://www.ncbi.nlm.nih.gov/pmc/tools/openftlist/). The annotations are automatically generated by matching the PDF format and the XML format of the articles in the PubMed Central Open Access Subset. More details are available in our paper ["PubLayNet: largest dataset ever for document layout analysis."](https://arxiv.org/abs/1908.07836), which was awarded the [best paper at ICDAR 2019](http://icdar2019.org/award/)!
