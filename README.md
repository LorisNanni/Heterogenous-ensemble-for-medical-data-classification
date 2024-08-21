# Heterogenous-ensemble-for-medical-data-classification
Heterogenous ensemble for medical data classification

In some datasets better convergence is obtained normalizing the data to [0,255], you can use the following code:
TR=data(idTR{fold},ord);%training set

TE=data(idTE{fold},ord);%test set

          
%normalization between [0,255]

massimo=max(TR)+0.00001;

minimo=min(TR);

training=[];

testing=[];

for i=1:size(TR,2)

    training(1:size(TR,1),i)=double(TR(1:size(TR,1),i)-minimo(i))/(massimo(i)-minimo(i));
    
end

for i=1:size(TE,2)

    testing(1:size(TE,1),i)=double(TE(1:size(TE,1),i)-minimo(i))/(massimo(i)-minimo(i));
    
end

TR=training*255;

TE=testing*255;

