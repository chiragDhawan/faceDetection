# faceDetection
#This is an eigenface implementation of the detection of faces
#The photographs were taken in controlled settings of 8 individuals and then the photographs were cropped and then they were converted to #gray and resized to a standard 100*100 using matlab.

#The data contained 262 images and it was spit into training, testing and validation with each containg 214, 24, 24 images #respectively

#The code to resize is as follows:

%    f=dir('G:\DataMiningData\Dataset\TrainingSet\*.jpg');
%        
%     for j=1:numel(f)    
%        I=double(imread(f(j).name));
%         I=reshape(I,[1 100*100]);
%         A(j,:)=I;
%        
%     end

# After the code was resized i
   %% Normalization of images
% for i=1:size(A,1)
%     minimum=min(A(i,:));
%     maximum=max(A(i,:));
%     A(i,:)=(A(i,:)-minimum)*255/(maximum-minimum);
% end;
% 
% %%%show a normalized image
% imshow(uint8(reshape(A(35,:),[100,100])))
% % 
% 
% 
% 
% %%%Mean image
% meanImage=mean(A,1);
% imshow(uint8(reshape(meanImage,[100,100])))


%    %% centering
%  for i=1:size(A,1)
%    A(i,:)=A(i,:)-meanImage;
%  end
% 
% [eigenVectors,score,eigenValues]=princomp(A);
% 
% 
% % % normalize the eigenvectors
% % 
%  for i=1:size(eigenVectors,2);
%      temp=eigenVectors(:,i);
%      eigenVectors(:,i)=eigenVectors(:,i)/sqrt(sum(temp.^2));
%  end
% % 

%  NumberOfEigenFaceVectors = 25;
%  eigenVectors = eigenVectors(:, 1:NumberOfEigenFaceVectors);
% % 
%%
% figure(1)
% title('Principal Components');
% for i=1:25
%     subplot(5,5,i);
%     imges=imagesc(reshape(eigenVectors(:,i),[100 100]));
%     
% end
% % 
% % 
%  % Now  project the images onto the principal eigenvectors
%   TrainingProjectedOntoPrinComp = A * eigenVectors;
% % 
% addpath('G:\DataMiningData\Dataset\ValidationSet');
% h=dir('G:\DataMiningData\Dataset\ValidationSet\*.jpg');
% for j=1:numel(h);
%     V=double(imread(h(j).name));
%     V=reshape(V,[1 100*100]);
%     ValidationImage(j,:)=V;
% end

%  ValidatingImages=ValidationImage;
% % % Normalization of the Validation images
% for i=1:size(ValidationImage,1)
%     minimum=min(ValidationImage(i,:));
%     maximum=max(ValidationImage(i,:));
%     ValidationImage(i,:)=(ValidationImage(i,:)-minimum)*255/(maximum-minimum);
% end;

% % Subtracting the mean from the ValidationImage
% 
% 
%  for i=1:size(ValidationImage,1)
%    ValidationImage(i,:)=ValidationImage(i,:)-meanImage;
%     end
% 
% % %%% Projecting Validaion vectors on to eigenface space
% 
%%%euclidean distance  
% for i=1:size(ValidationImage,1);
%     ValidationProjectedOntoPrinComp=ValidationImage(i,:) * eigenVectors  ;
%     euclideanSimilarity=arrayfun(@(func) norm(TrainingProjectedOntoPrinComp(func,:)-ValidationProjectedOntoPrinComp),1:size(A,1));
%     %% check for minimum distance
%     [Score(i),IndexOfTrainImage(i)]=min(euclideanSimilarity);
%     [S,Q]=sort(euclideanSimilarity);
%     
%     Indices(i,:)=Q(1:3);
% 
% end

%%%%checking for 1 nearest neighbour
% for i=1:size(ValidatingImages,1)
% j=0;
% figure(i);
% 
% 
% subplot(2,1,1);
% imshow(uint8(reshape(ValidatingImages(i,:),[100,100])));
% title('Validation Image')
% 
% 
% 
% 
% subplot(2,1,2)
% imshow(uint8(reshape(trainingImages(IndexOfTrainImage(i),:),[100,100])));
% title('Training Image Recognized');
% end



% 


%%%checking for 3 nearest neighbour
% for i=1:size(ValidationImage,1)
% j=0;
% figure(i);
% 
% j=j+1;
% subplot(4,1,1);
% imshow(uint8(reshape(ValidatingImages(i,:),[100,100])));
% title('Validation Image')
% 
% j=j+1;
% 
% for z=1:3,
%     subplot(4,1,z+1)
% imshow(uint8(reshape(trainingImages(Indices(i,z),:),[100,100])));
% title('Training Image Recognized');
% end
% end
% 
% 
% 
%%
% % %  %% Now testing the test images
      
% % %  %% Now testing the test images
        
% addpath('G:\DataMiningData\Dataset\TestSet');
% g=dir('G:\DataMiningData\Dataset\TestSet\*.jpg');
% for j=1:numel(g);
%     T=double(imread(g(j).name));
%     T=reshape(T,[1 100*100]);
%     testImage(j,:)=T;
% end
%  testingImages=testImage;
% % % Normalization of the test images
% for i=1:size(testImage,1)
%     minimum=min(testImage(i,:));
%     maximum=max(testImage(i,:));
%     testImage(i,:)=(testImage(i,:)-minimum)*255/(maximum-minimum);
% end;

% % Subtracting the mean from the TestImages
% 
% 
%  for i=1:size(testImage,1)
%    testImage(i,:)=testImage(i,:)-meanImage;
%     end
% % 
% % %%% Projecting test vectors on to eigenface space
% 
% % euclidean distance
% for i=1:size(testImage,1);
%     TestProjectedOntoPrinComp=testImage(i,:) * eigenVectors  ;
%     euclideanSimilarity=arrayfun(@(func) norm(TrainingProjectedOntoPrinComp(func,:)-TestProjectedOntoPrinComp),1:size(A,1));
%     %% check for minimum distance
%     [Score(i),IndexOfTrainImages(i)]=min(euclideanSimilarity);
%     
% 
% end


% 
% % 
for i=1:size(testImage,1)
j=0;
figure(i);


subplot(2,1,1);
imshow(uint8(reshape(testingImages(i,:),[100,100])));
title('Testing Image')




subplot(2,1,2)
imshow(uint8(reshape(trainingImages(IndexOfTrainImages(i),:),[100,100])));
title('Training Image Recognized');
end

% 
% % 
% % 

